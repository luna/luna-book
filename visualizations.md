#Visualizations in Luna

Visualization in Luna is a widget responsible for displaying data in certain way in Node Editor. In Luna Studio we have few types of visualizations available for different types of data, i.e. echarts plots for lists.
To show the visualziation you have to click the eye icon on the right side of node name:
![](/assets/visualizations_eye_icon.png)
To choose the different type of visualization you can drop a list of possible to use types of visualizations.
![](/assets/visualizations_drop_list.png)

#Creating custom visualizations

To create custom visualization for your project you need to add visualizers folder in the root of the project folder:
```
MyProject/
	MyProject.lunaproject
	src/
    	Main.luna
	visualizers/
    	example/
        	config.js
        	example.css
        	example.html
        	example.js       	 
```
It contains few files:
    - `min.js` - minified JS file with library you want to connect with visualization (not included in visualizer template)
    - `config.js` - list of constructors for visualization to be active and types, calling proper html when types matches
    - `example.js` - event listeners for different events (message, resize - full screen and load). All the important things will happen here.
    - `example.css` - basic  css file for visualization
    - `example.html` - html file with all css and js imports and custom div id predefined.
You can download template `visualizers` folder from https://github.com/luna/visualizers-template/archive/master.zip
At this moment you can not change the size of the visualization, it is fixed to 300 x 300 px. If you hold `space` key the visualization will be maximized to the Node Editor size.


Communication between Luna and visualization is through JSON structures. Simplest way to create custom visualization, on Luna side, is creating proper type for a visualization. Let's assume we want to connect with a new plotting library written in JS. The JS part of visualization is expecting id of html object in which it will show the result and plot definition. The chart object will contain two nested objects: data series called `data` and `type` with type of plot. The datatype looks like:
```
class PlotType:
	Bar
	Pie
	Scatter

class DataSeries:
	data:: List Int
	type:: PlotType
```
Data series can be an Int list and the plot type can be `Scatter` , `Pie` or `Bar`. I will create separate type called `PlotType`. Additional helpers for `DataSeries` are defined to make creating JSON more simple and straightforward. To use it in JS we need to define `toJSON` method on each of the classes.
```
class PlotType:
	Bar
	Pie
	Scatter

	def toJSON:
    	Bar: 	JSONString "bar"
    	Pie: 	JSONString "pie"
    	Scatter: JSONString "scatter"

class DataSeries:
	DataSeries
	DataSeriesVal:
    	data:: List Int
    	type:: PlotType

	def getData: case self of
    	DataSeriesVal data _: data
	def getType: case self of
    	DataSeriesVal _ type: type

	def toJSON:
    	JSON.empty . insert "data" self.getData . insert "type" self.type
```
As you can see I don't have to define `toJSON` method for `List Int` separately. It is predefined in a `List` class in Luna.Base.
To read the data in JS in `example.js` file you need to unpack the JSON:
```
  window.addEventListener("message", function (evt) {
	if(evt.data.data) {
    	data = JSON.parse(evt.data.data);
    	dataSeries = data;
    	ExamplePlottingLibrary.plotCommand("example_div", dataSeries)
	};
	}
```
If you want the visualization behave in certain way on "resize" or "load" message you can define it in the same file in proper event listeners (look at the template - https://github.com/luna/visualizers-template/blob/master/example/example.js).

To set on which type visualization should be shown we need to add a constructor to constructors list in `config.js` file:
```
module.exports = function (type) {
    var examplePattern =
        { constructor: ["DataSeries"], fields: [{constructor: ["Int", "Real"], fields: { any: true }}]
        };

    if (cfgHelper.matchesType(type, examplePattern))
        {
            return [{name: "example", path: "example.html"}]
        }
    else
        return [];
};
```
If a node will have `DataSeries` type the `example` visualization will be shown in drop-down menu on the left side of the node.

To use such defined visualization in your project you need to define the list of ints which will be your data: (screen z list of ints node)
and a new node packing it in the `DataSeries` type: (another screen screen)

And voila! you can see your plot in Node Editor!

To see more visualizations implementation please visit:
https://github.com/luna-packages/PlotLu

## Visualizations in Luna

Visualization in Luna is a widget responsible for displaying data in certain way in Node Editor. In Luna Studio we have few types of visualizations available for different types of data, i.e. echarts plots for lists.
To show the visualziation you have to click the eye icon on the right side of node name:

![](/assets/visualizatons_eye_icon.png)

To choose the different type of visualization you can drop a list of possible to use types of visualizations (hover the mouse cursor over a triangle on the left side of the node):

![](/assets/visualizatons_dropdown.png)

## Creating custom visualizations

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
* `config.js` - module responsible for checking if your visualization is able to present data of current type and presenting to gui all compatible presentation forms
* `example.js` - event listeners for different events (like `message`, `resize` and `load`). All the important things will happen here.
* `example.css` - css styling for visualizer
* `example.html` - html file with all css and js imports.

You can download template `visualizers` folder from https://github.com/luna/visualizers-template/archive/master.zip
At this moment you can not change the size of the visualization, it is fixed to `300 x 300 px`, but if you hold `space` key the visualization will be maximized to the Node Editor size.

Let's try to add a visualization for a list of Ints. `Main.luna` will be:
```
def main:
    list1 = [1,2,3,4,5,6]
    None
```
Communication between Luna and visualization is through JSON structures. `toJSON` method for a list is predefined in `Base.luna` so it is not nescessary to define it in our project.
To read the data in JS in `example.js` file you need to unpack the JSON and visualize the data:
```
window.addEventListener("message", function (evt) {
    if(evt.data.data) {
        data = JSON.parse(evt.data.data);
        document.getElementById('example_div').innerHTML = "<span>" + data.toString() + "</span>";
    };
    }
```
In this case visualization will show the numbers from the list.

If you want the visualization behave in certain way on "resize" or "load" message you can define it in the same file in proper event listeners (look at the template - https://github.com/luna/visualizers-template/blob/master/example/example.js).

To set on which type visualization should be shown we need to add a constructor to constructors list in `config.js` file. The return value is a list of all visualizers served by this packet:
```
module.exports = function (type) {
    var examplePattern =
        { constructor: ["List"], fields: [{constructor: ["Int", "Real"], fields: { any: true }}]
        };

    if (cfgHelper.matchesType(type, examplePattern))
        {
            return [{name: "example", path: "example.html"}]
        }
    else
        return [];
};
```
With this config the visualizer will show for list of Ints or Reals as the `example` visualizer. The visualization will print all the numbers as a String:
![](/assets/visualizations_list_of_ints.png)

### Connecting visualizations with plotting library

Let's assume we want to connect with a new plotting library written in JS. It will work for a list of Ints like the example above. This time it will be able to show multiple lists of Ints on a single plot with different plots types like `Scatter`, `Pie` or `Bar`. The JS part of visualization is expecting a list of data series. Each data serie will contain two nested objects: list of  called `data` and `type` with a plot type. The datatype looks like:
```
class PlotType:
    Bar
    Pie
    Scatter

class DataSeries:
    DataSeries
    DataSeriesVal:
        data:: List Int
        type:: PlotType
```
To use it in JS we need to define `toJSON` method on each of the classes.
```
class PlotType:
    Bar
    Pie
    Scatter

    def toJSON: case self of
        Bar:     JSONString "bar"
        Pie:     JSONString "pie"
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
        JSON.empty . insert "data" self.getData . insert "type" self.getType
```
Plot will be a simple list of `DataSeries`, so the class for final type to plot with `toJSON` method is:
```
class Plot:
    Plot
    PlotVal (List DataSeries)
    def toJSON: case self of
        PlotVal ds: ds.toJSON
```
In `config.js` file the visualiztion should react on the `Plot` type like in example above for `List`. Instead of printing a list of Ints in `example.js` this time a plotting function will be called.

If a node will have `Plot` type the `example` visualization will be shown in drop-down menu on the left side of the node.

To use such defined visualization in your project you need to define the list of Int which will be your data:
![](/assets/visualizations_list.png)
and a new node packing it in the `DataSeries` type:
![](/assets/visualizations_dataseries.png)
and then into `Plot` type with single element list contains your data:
![](/assets/visualizations_plot.png)

`main` function will be:
```
def main:
    list1 = [1,2,3,4,5,6]
    ds = DataSeriesVal list1 Scatter
    PlotVal [ds]
```
The library should be put as minified JS file into `MyProject/visualizers/example/example.min.js`.

And voila! you can see your plot in Node Editor!

To see more visualizations implementation please visit:
https://github.com/luna-packages/PlotLu

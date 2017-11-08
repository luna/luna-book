# Visual representation

Luna is a data processing language and like every language Luna provides a syntax. However, in contrast to majority of languages Luna has more than one syntax representation – visual and textual. This chapter describes the former – visual data flow graph. We have designed the visual representation to be 

While designing the visual representation we've put an enormous emphasis on productivity and ergonomics. Every element and every action was carefully designed to allow you express your thoughts easily, understand the results rapidly and clearly see all the data transformations. You have to learn how to "speak this language", however it's worth doing, even hardcore coders much prefer using Luna for building high-level data processing workflows than writing code. We are on a mission to constantly improve how you work with Luna, so your feedback and suggestions are very important to us. If you have any ideas related to how the visual representation works, [tell us about it](http://luna-lang.org/forum)!


## Navigation

Luna Visual Editor is a two dimensional canvas allowing you for fluid navigation so you can always focus on what is important at the moment. You can:
* **pan** the view using two fingers drag gesture or the middle mouse button;
* **zoom** the view using pinch gesture or the right mouse button;
* **select nodes** by clicking them or using left mouse button to draw selection area starting from the background;
* **dive into nodes** by double clicking them;
* **view parent nodes** by double clicking on the background or using the breadcrumb controls on top of the Visual Editor.


## Nodes
A node is the most primitive entity, which connected with other nodes form the data flow graph. 


### Value nodes
Value nodes are the most common node types. They represent any valid Luna value, including data processing functions. From the high perspective, a value node can generate data, modify it or store in a database. Value nodes consist of several visual elements:

###### Node expression (the node name) <span class="uiref">1</span> 
The node expression, sometimes referred to as the node name, is any valid Luna code, in particular a function name. For example, a node which adds together two objects is named `+`. 

###### Input ports <span class="uiref">2</span> and output ports <span class="uiref">3</span>
Ports are the data node's communication gates. Data flows into input ports on the left side, is processed according to the node expression and the result flows out from the output ports on the right side. Port colors indicate what type of data flows trough them. You will learn more about data types in the [Types 101](dummy.md) chapter.

###### Self port<span class="uiref">4</span> 
Luna is an object oriented language. It means that every data that flows between nodes is not just information, it can also respond to your commands. You can for example tell a car to stop, a dog to bark, a number to increase or a list to sort its items. If a data is connected to self port, then the node's expression tell it what to do. A rule of thumb is that if you want to process a data, connect it to the self port. You will learn in detail about it in the [Making our own type](dummy.md) chapter.

![](/assets/placeholder.jpg)


### Reference nodes
Sometimes you don't want to process data, you want to inspect and deconstruct it instead. Nodes that do not affect the data, but just allow you to look into it are called reference nodes. They usage is covered in detail in the [Pattern matching](dummy.md) chapter. They contain a special target port <span class="uiref">1</span> which accepts data that you want to inspect. 

![](/assets/placeholder.jpg)



## Creating nodes

Nodes are always created with the help of [Luna Explorer](explorer.md), however, there are several options to launch it and guide towards our intentions:

* press the <kbd>tab</kbd> key to search across all available components;
* click on the input or output port with the right mouse button to guide the Explorer to look for functions capable of processing its type of data;
* select a node and then press the <kbd>tab</kbd> key to guide the Explorer to look for functions capable of processing its results.



## Connecting and disconnecting nodes
To establish a new flow of data, you can connect an output port to either an input port or a self port. There is no a single best way to do it. It depends on your preferences, graph complexity, zoom level and much more. Luna provides you with several alternative ways to connect and disconnect nodes, so you can choose the one which suits you most in a given situation.


###### Connecting nodes

* **By drag**  
  Press an output port, drag and drop it over desired input or self port. Alternatively you can press the input port, drag and drop it over desired output port. You cannot, however, start the connection by pressing the self port – pressing the node body selects it instead. Drop over the background to cancel.
  ![](/assets/placeholder2.jpg)

* **By click**  
  Click (press and release) an output port, the connection will follow your mouse until you click again. Click on the desired input port or self port to create new connection or click on the background to cancel. You can also click on the input port and then on the output port. Click on the background to cancel.
  ![](/assets/placeholder2.jpg)

* **Using connection pen**
  Press and drag on the stage while holding the <kbd>ctrl</kbd> key to draw a green stroke using the connection pen. Connection pen will automatically connect all nodes on its way. Currently if connection pen connects two nodes, the results from the first one will be connected to the first input of the second node. This behavior will be enhanced soon and Luna will try to create connection between ports with matching types.
  ![](/assets/placeholder2.jpg)

* **On creation**
  Select a node before opening Explorer to guide it to search for functions associated with the node's results and automatically connect the results to the self port of newely created node.
  ![](/assets/placeholder2.jpg)



###### Disconnecting and reconnecting nodes

* **By drag**
  Press one of connection's ends to disconnect it and enter "connecting by drag" mode. You can drag and drop it over other port to reconnect or drop on the background to remove the connection.
  ![](/assets/placeholder2.jpg)

* **By click**
  Click one of connection's ends to disconnect it and enter "connecting by click" mode. You can click on other port to reconnect or click on the background to remove the connection.
  ![](/assets/placeholder2.jpg)

* **Using connection pen**
  Press and drag on the stage while holding both <kbd>ctrl</kbd> and <kbd>shift</kbd> keys to draw a red stroke using the connection pen. Connection pen will automatically break every connection it crosses.
  ![](/assets/placeholder2.jpg)















  for now just think of data flowing between nodes like objects capable to take action. If you connect data to the self port, the node expression tells it what to do. If you for example connect list of numbers to a self port of node `sort`   It means that every data is a combination of information and behavior. that flows between nodes does not only represent data, but also  , which means that you 
In Luna every data is an object, which

The self port<span class="uiref">4</span> is a special input port. Luna is an object oriented language, which means that you should think of data flowing between nodes like objects which could perform actions. If such an object flows into the self port, the nodes expression tells him what to do



Node body could be displayed in one of two forms – compact and detailed. The detailed view allows to interactively change node parameters and will be covered later. The node body consist of input ports <span class="uiref">3</span> and output ports <span class="uiref">4</span>. Ports are like gates. 

The colors of ports and connections indicate what type of data flows trough them. You can learn more about data types in the following [Types 101](dummy.md) chapter.

![](/assets/placeholder.jpg)




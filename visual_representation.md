# Visual representation

Luna is a data processing language and like every language Luna provides a syntax. However, in contrast to majority of languages Luna has more than one syntax representation – visual and textual. This chapter describes the former – visual data flow graph.

## What is a node

A node is the most primitive entity, which connected with other nodes form the data flow graph. From the highest perspective, a node is a data processing function, which can generate data, modify it or store in a database. Nodes consist of several visual elements, however not all of them all always accessible.

###### Node expression (the node name) 
The node expression <span class="uiref">1</span>, sometimes referred to as the node name, is any valid Luna code, in particular a function name. For example, a node which adds together two objects is named `+`. 

###### Input and output ports
Ports are the data node's communication gates. Data flows into input ports on the left side <span class="uiref">2</span>, is processed according to the node expression and the result flows out from the output ports on the right side<span class="uiref">3</span>. 



Node body could be displayed in one of two forms – compact and detailed. The detailed view allows to interactively change node parameters and will be covered later. The node body consist of input ports <span class="uiref">3</span> and output ports <span class="uiref">4</span>. Ports are like gates. 

The colors of ports and connections indicate what type of data flows trough them. You can learn more about data types in the following [Types 101](dummy.md) chapter.

![](/assets/placeholder.jpg)


## Creating nodes

Nodes are always created with the [Luna Explorer](explorer.md), however, there are several options to launch it and guide towards our intentions:

* press the <kbd>tab</kbd> key to search across all available functions;
* click on the input or output port with the right mouse button to guide the Explorer to look for functions capable of processing its type of data;
* select a node 

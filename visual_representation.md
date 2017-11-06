# Visual representation

Luna is a data processing language. Like every language, Luna provides a syntax, however, in contrast to majority of languages Luna provides two equivalent syntax forms – visual and textual. This chapter describes the former one – visual data flow graph.

## What is a node

A node is the most primitive entity, which connected to other nodes form the data flow graph. From the highest perspective, a node is a data processing function. In particular it can generate data, modify it or store it in a database. 

Nodes consist of an expression field <span class="uiref">1</span> and node body <span class="uiref">2</span>. The expression field is any valid Luna code, in particular a function name, sometimes referred to as the node name. For example, a node which adds together two objects is named `+`. Node body could be displayed in one of two forms – compact and detailed. The detailed view allows to interactively change node parameters and will be covered later. The node body consist of input ports <span class="uiref">3</span> and output ports <span class="uiref">4</span>. Ports are like gates. Data flows into input ports, is processed according to the node expression and the results flow out of the output ports. 

The colors of ports and connections indicate what type of data flows trough them. You can learn more about data types in the following [Types 101](dummy.md) chapter.

![](/assets/placeholder.jpg)


## Creating nodes

Nodes are always created with the [Luna Explorer](explorer.md), however, there are several options to launch it and guide towards our intentions:

* press the <kbd>tab</kbd> key to search across all available functions;
* click on the input or output port with the right mouse button to guide the Explorer to look for functions capable of processing its type of data;
* select a node 

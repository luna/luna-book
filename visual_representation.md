# Visual representation

Luna is a data processing language. Like every language, Luna provides a syntax, however, in contrast to majority of languages Luna provides two equivalent syntax forms – visual and textual. This chapter describes the former one – visual data flow graph.

## What is a node

A node is the most primitive entity, which connected to other nodes form the data flow graph. From the highest perspective, a node is a data processing function. In particular it can generate data, modify it or store it in a database. 

Nodes consist of an expression field <span class="uiref">1</span> and node body <span class="uiref">2</span>. The expression field is any valid Luna code, in particular a function name, sometimes referred to as the node name. For example, a node which adds together two objects is named `+`. Node body could be displayed in one of two forms – compact and detailed. The detailed view allows to interactively change node parameters and will be covered later. The node body consist of input ports <span class="uiref">3</span> and output ports <span class="uiref">4</span>. Ports are like gates. Data flows into input ports, is processed according to the node expression and the results flow out of the output ports. 

![](/assets/placeholder.jpg)


## Creating nodes

Nodes are 


could be displayed
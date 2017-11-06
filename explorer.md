# The Luna Explorer

The Luna Explorer is a sophisticated fuzzy search engine integrated with an expression editor. It allows you to search for components, create them and browse their documentation. The Explorer is context-aware, which means that it tries to predict your intention and adjust the search results accordingly. 

### Accessing the Luna Explorer

In order to access the Explorer place your mouse over the data flow editor and press the <kbd>tab</kbd> key. You can close the Explorer by pressing either the <kbd>escape</kbd> key or the <kbd>tab</kbd> key again, however the later is allowed only if no input was provided so far. 

The Explorer consists of three panels – expression editor <span class="uiref">1</span>, suggestions list <span class="uiref">2</span> and documentation view<span class="uiref">3</span>. The expression editor is always active and listens for your input, so you can start typing as soon as the explorer appears on your screen.

The circle below the Explorer is called a node. It is visualization of the component you are going to create. You will learn more about nodes in the following chapter.

> **[info] Improvements ahead!**
>
> The Explorer is currently available only from within the data flow editor. It will be also integrated with the code editor in the future.


![](/assets/placeholder.jpg)


## Result scoring
The suggestions are scored based on the current expression context and the match accuracy. The algorithm details are beyond the scope of this book, however, there are few important rules you should learn to use the Explorer more efficiently:

* Luna uses the [camel case naming convention](dummy.md) for it's identifiers. The Explorer splits the known identifiers by upper case letters into separate words and prefers full-word matches over sub-string matches.
Example: Typing `"iden"` will match `"superIdentifier"` better than `"evidence"`.
* The Explorer is both case and accent insensitive, however, it will score exact match a little better than misspelled one.
Example: Typing `"fooBar"` will match `"fooBar"` (exact match) better than `"foobar"`.
* The Explorer will accept misspelled words with appropriate score penalty.
Example: typing `"sibdi"` will match `"subdivide"` with major score penalty.


## What's next?
The Luna explorer is a very powerful tool. We will be introducing its features gradually in the following chapters. 




ooooooooooooooooooooooooooooooooooooooooooooooooooo
END





### Searching

###### The current scope
The default behavior of the Explorer is to lookup the available components by name. More precisely, the Explorer searches for modules, data constructors, and functions accessible within the scope. You will learn more about these terms in the following chapters, you don't need to understand what they are in Luna now.

Luna is a case sensitive language. It means that upper and lower case letters are distinguishable. In particular, data constructor and module names start with upper case letter, while function names with lower case one. You can guide the Explorer into the right direction – if you start typing using the upper case letter, the Explorer will favor modules and data constructors in its search results. 

  You do not need to know what these things mean, it's ok for now to remember  and modules. In order to guide the Explorer that you are looking for a module, start your search with a capital letter. See the [Luna naming convention](dummy.md) for more details.




The Luna Explorer is an interactive expression editor integrated with a context-aware fuzzy search engine for Luna libraries and documentation. It also facilitates creating new nodes in the visual data flow graph editor. 





  libraries and documentation and It is the primary tool for building 

  for Luna libraries and documentation. It also facilitates creating new nodes in the visual data flow graph editor. 





###### Searching for functions and modules
The default behavior of the Explorer is to search for functions and modules. In order to guide the Explorer that you are looking for a module, start your search with a capital letter. See the [Luna naming convention](dummy.md) for more details.

###### Searching for methods
In order to get method suggestions you have to provide the Explorer with information what is the data type you are looking methods for. The easiest way to do it is to select 
The Explorer would score methods better if either a node was selected before it was opened or you are currently editing a method name in the expression editor. Only methods of the result <...> would match here. 

![](/assets/placeholder.jpg)


## Connecting nodes


#### Creating nodes 

Type `7` or any other lucky number and press <kbd>enter</kbd> to confirm your choice. A blue circle appears on the screen <span class="uiref">1</span>. It is called a "node". You will learn more about both the Node Searcher and nodes in the following chapters. For now just remember that node is a function, that you feed with data from the left side and outputs result from the right side. A number does not need any input, it just returns itself as a result, thus we do not need to connect anything to it's left side. It's color indicates the type of data it processes. Numbers are blue. Simple, isn't it? 

![](/assets/placeholder.jpg)


#### Connecting nodes

Next press the <kbd>tab</kbd> key again and type `13` or any other unlucky number. Press the <kbd>enter</kbd> key. You should see 2 circles on the screen. You can press and drag them to arrange them freely in the space. Let's arrange them vertically! 

Select the node with lucky number and press the <kbd>tab</kbd> key again. If a node is selected when Node Searcher opens, it tries to search for associated functions first. As you can see, a lot of mathematical functions are displayed now. Type `+` and press <kbd>enter</kbd>. A new node appears <span class="uiref">1</span>. This time however, it is connected to our lucky node. The connection <span class="uiref">2</span> indicates the flow of data. It just means that the number `7` flows from its creator into the `+` node. To connect the second number, hover over it's output port <span class="uiref">3</span> and either drag it to input port of `+` node <span class="uiref">4</span> or click on each port respectively.

![](/assets/placeholder.jpg)


#### Updating parameters

As you can see, each node displays it's results below it's visual representation <span class="uiref">1</span>. An important thing to note here is that Luna works in a reactive way, so keeps all results always up to date. Let's click on the lucky number node and press <kbd>enter</kbd> key. The node will expand from its minimal representation to a full one <span class="uiref">2</span> giving you access to interactive controls - a number slider in this example. Change the slider and observe how the results update on the fly! 

We strongly encourage you to play with it now. Try to read a text file from disk, divide it into list of words and count how many words there are! Hint: `readFile` and `words` are your friends!


> **[info] Improvements ahead!**
>
> Currently the way Luna updates the results is sub-optimal. After changing the value or creating a new node, Luna checks the whole program from scratch, including polymorphic type resolution and performing optimizations on the low level graph representation. You can observe it when using the slider. 
>
>Keep in mind that it affects only the interactive UI performance, not the graph performance in general. For example, if your graph is already created and receives thousands of objects from a web socket, they will be processed without performance overhead, because the graph will be type checked and optimized upfront.
>
>We are preparing new release, which will solve this issue and allow both value change as well as graph modification to perform almost instantly.

![](/assets/placeholder.jpg)

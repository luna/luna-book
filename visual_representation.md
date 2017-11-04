# Ready, set, go!

It's time to make our hands dirty with Luna! The first thing we're going to do is to create a simple data flow graph, which will create two numbers and then add them together!

# Luna Explorer

The Luna Explorer is a context-aware fuzzy search engine and interactive expression editor. The Explorer is currently available only within the data flow editor.

###### Result scoring
The Luna Explorer uses sophisticated fuzzy search algorithm allowing searching for methods, functions, modules, libraries, commands and more. The results are sorted by their score based on the current context and the match accuracy. The algorithm details are beyond the scope of this book, however, there are few important rules you should know:

  * Luna uses the [camel case naming convention](dummy.md) for it's identifiers. The Explorer splits the identifiers by upper case letters into separate words and prefers full-word matches over sub-string matches. 
  Example: Typing `"iden"` will match `"superIdentifier"` better than `"evidence"`.
  * The Explorer is both case and locale insensitive, however, it will score exact match a little better than misspelled one.
  Example: Typing `"fooBar"` will match `"fooBar"` (exact match) better than `"foobar"`. 
  * The Explorer will accept misspelled words with appropriate score penalty.
  Example: typing `"sibdi"` will match `"subdivide"` with major score penalty.


###### Accessing the Luna Explorer
In order to access the Luna Explorer place your mouse over the data flow editor and press the <kbd>tab</kbd> key. You can close the Explorer by pressing the <kbd>tab</kbd> key again if no input was provided or the <kbd>escape</kbd> key otherwise. The Explorer consists of three panels – input expression editor <span class="uiref">1</span>, result list <span class="uiref">2</span> and documentation view<span class="uiref">3</span>. You can start typing as soon as the Explorer appears on your screen. The input expression editor is always active and listens for your input until the Explorer is closed.


###### Searching for functions and modules

The default behavior of the Explorer is to search for functions and modules.  After opening the explorer you can type the desired name. The results will update on 

A Node Searcher should appear on the screen <span class="uiref">2</span>. It allows you to filter available functions and libraries by their names.

###### Searching for methods
The Explorer would score methods better if a node was selected before it was opened or the expression being currently edited is preceded by the access operator `.`. Only methods of the result <...> would match here. 

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

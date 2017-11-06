# The Luna Explorer

The Luna Explorer is a sophisticated fuzzy search engine integrated with an expression editor. It allows you to search for components, create them and browse their documentation. The Explorer is context-aware, which means that it tries to predict your intention and adjust the search results accordingly. 

### Accessing the Luna Explorer

In order to access the Explorer place your mouse over the data flow editor and press the <kbd>tab</kbd> key. You can close the Explorer by pressing either the <kbd>escape</kbd> key or the <kbd>tab</kbd> key again, however the later is allowed only if no input was provided so far. 

The Explorer consists of three panels – expression editor <span class="uiref">1</span>, suggestions list <span class="uiref">2</span> and documentation view<span class="uiref">3</span>. The expression editor is always active and listens for your input, so you can start typing as soon as the explorer appears on your screen.

The circle below the Explorer is called a node<span class="uiref">4</span>. It is a preview of the component you are going to create. You will learn more about nodes in the following chapter.

> **[info] Improvements ahead!**
>
> The Explorer is currently available only from within the data flow editor. It will be also integrated with the code editor in the future.


![](/assets/placeholder.jpg)


## Using the Explorer
The Explorer will provide suggestions on the fly while you are typing. It will search Luna libraries for components that match your query. The component on the bottom on the list is selected by default. You can move the selection by using the up <kbd>up arrow</kbd> and <kbd>down arrow</kbd> keys. To confirm your choice and create the selected component, press the <kbd>enter</kbd> key.

However, there are sometimes situations when you want to create components that are not available on the suggestion list. A good example is when you want to refer to a component that does not yet exist and you are going to create it soon. Another possibility is that Luna didn't get enough information to provide you with the complete components list, which could happen when you are working on polymorphic data. You will learn more about polymorphism later, for now just remember, that you can use the <kbd>down arrow</kbd> key to move the selection from the suggestions list onto the expression editor and press the <kbd>enter</kbd> key to create component named exactly as you have typed.


## Searching possibilities
The Luna explorer provides several context-aware searching utilities. We will be introducing its possibilities gradually in the following chapters, however, don't hesitate to check them out now:

* [Searching by a method name](dummy.md)
* [Searching by a type signature](dummy.md)
* [Browsing available libraries and modules](dummy.md)


## Result scoring (advanced)
The suggestions are scored based on the current expression context and the match accuracy. The algorithm details are beyond the scope of this book, however, there are few important rules you should learn to use the Explorer more efficiently:

* Luna uses the [camel case naming convention](dummy.md) for it's identifiers. The Explorer splits the known identifiers by upper case letters into separate words and prefers full-word matches over sub-string matches.
Example: Typing `"iden"` will match `"superIdentifier"` better than `"evidence"`.
* The Explorer is both case and accent insensitive, however, it will score exact match a little better than misspelled one.
Example: Typing `"fooBar"` will match `"fooBar"` (exact match) better than `"foobar"`.
* The Explorer will accept misspelled words with appropriate score penalty.
Example: typing `"sibdi"` will match `"subdivide"` with major score penalty.





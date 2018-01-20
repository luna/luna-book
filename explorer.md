# The Luna Explorer

The Luna Explorer is a sophisticated fuzzy search engine integrated with an expression editor. It allows you to search for components, create them and browse their documentation. The Explorer is context-aware, which means that it tries to predict your intention and adjust the search results accordingly. 

### Accessing the Luna Explorer

In order to access the Explorer place your mouse over the data flow editor and press the <kbd>tab</kbd> key. You can close the Explorer by pressing either the <kbd>escape</kbd> key or the <kbd>tab</kbd> key again, however the latter is allowed only if no input was provided so far. 

The Explorer consists of three panels – expression editor, suggestions list and documentation view. The expression editor is always active and listens for your input, so you can start typing as soon as the explorer appears on your screen.

The circle below the Explorer is called a node. It is a preview of the component you are going to create. You will learn more about nodes in the following chapter.

![](/assets/explorer.png)


## Using the Explorer
The Explorer will search Luna libraries for components that match your query. The provided query does not need to be precise – it is usually sufficient to provide only a part or several parts of the name you are looking for.

The Explorer will provide suggestions on the fly while you are typing. The best match will be displayed on the bottom of the list and will be selected by default. You can move the selection by using the up <kbd>up arrow</kbd> and <kbd>down arrow</kbd> keys. To confirm your choice and create the selected component, press the <kbd>enter</kbd> key. To accept the hint and continue typing after that, prass <kbd>tab</kbd>.

However, there are sometimes situations when you want to create components that are not available on the suggestion list. A good example is when you want to refer to a component that does not yet exist and you are going to create it soon. Another possibility is that Luna didn't get enough information to provide you with the complete components list, which could happen when you are working on polymorphic data. You will learn more about polymorphism later, for now just remember, that you can use the <kbd>down arrow</kbd> key to move the selection from the suggestions list onto the expression editor and press the <kbd>enter</kbd> key to create component named exactly what you have typed.

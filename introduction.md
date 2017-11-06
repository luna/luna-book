# What is Luna?

Luna is an open source, [WYSIWYG](https://en.wikipedia.org/wiki/WYSIWYG) data processing language. Its goal is to revolutionize the way people are able to gather, understand and manipulate data.

Luna targets domains where data processing is the primary focus, including data science, machine learning, IoT, bioinformatics, computer graphics or architecture. Each domain requires a highly tailored data processing toolbox and Luna provides both an unified foundation for building such toolboxes as well as growing library of existing ones. At its core, Luna delivers a powerful data flow modeling environment and an extensive data visualization and manipulation framework.

![](/assets/screen1.png)


## The rise and fall of DSLs
> **The limits of my language are the limits of my world.**


The variety of domain specific requirements contributed significantly to the rise of [Domain Specific Languages (DSLs)](https://en.wikipedia.org/wiki/Domain-specific_language). If you are a software developer, you probably recognize DSLs with their most popular form, a highly specialized subset of textual programming languages. However, the definition of a DSL is much broader than that. Domain specific language is a highly tailored textual or visual interface for manipulating data in a particular domain. Rich graphical user interfaces designed to work with domain specific data like UML diagramming, interactive plotting or music processing should be considered DSLs too. A good example is the most common DSL used by graphic designers nowadays – a digital canvas with an associated toolbox of layers, brushes, shapes, filters, etc.


#### Language design principles

A well-designed domain specific language, or a language in general, empowers people with the ability to both express their thoughts in a rapid and concise way as well as understand the feedback response easily. It is especially important to research because it directly affects how fast you can iterate – test new ideas and understand intermediate results. Fast iterations make it possible to test a wider range of parameters including those that should not work at first glance, allowing you to much better understand the domain you are investigating. Thus the language design directly affects not only the total time needed to solve a problem in a non-linear way, it often is the key to find the solution at all. 

An important question emerges – what is a good language? Are there any guidelines every domain specific language should follow? We believe there are two basic principles:

* **People need an immediate connection to what they are making**  
  This principle was first publicly introduced by Brett Victor, a human-computer interaction visionary, during his talk [Inventing on Principle](https://vimeo.com/36579366). Any violation of this principle alienates the user from the actual problems he is trying to solve, which consequently decreases the understanding and increases the number of mistakes.

* **People cannot be limited by the tool they are using**  
  People tend to reject any tool which obviously limits their expressiveness. This is the exact reason why so many WYSIWYG solutions, like website creators, game creators or visual programming languages never catch up. Any DSL more complex than a WYSIWYG text editor can easily violate this principle by providing its users with a too limited set of predefined, high-level components. Even if these components can be extended by writing code, the need to resort to some underlying programming language spoils the design and makes it unusable for a less technical audience.


#### Principle violation

Violation of any of these principles always leads to a sub-optimal solution. Let's consider the graphic design again. Is using Photoshop always better than writing HTML, Sass and JavaScript code? Arguably. These solutions violate the first and the second principle respectively. Photoshop provides a WYSIWYG digital canvas with a limited set of predefined, hardly extendable tools. HTML, Sass and JavaScript, on the other hand, provide a text interface and thus alienate the user from its real creation, but do not set a tight restriction on the expressiveness. Let's consider two use cases:

* A website design. There are five, evenly arranged items in the menu bar. If you want to add a new item and change the color palette of the website, all you have to do is to modify a single line in HTML and a color variable in Sass. No matter how complex the website is, every element will update automatically. Doing the same in Photoshop requires several orders of magnitude more time – create a new menu item, use an alignment tool to arrange the elements, manually change the colors and probably re-apply some transformations and filters in more complex website areas.

* An artistic painting. Using HTML, SVG and Sass within a text editor to express an artistic vision would hardly be possible. The more creative and discoverable the process is, the more important the WYSIWYG toolset and instant feedback loop become.

Would it be possible to fuse both approaches? It's not only possible, there are already solutions heading in the right direction. Think about Sketch, which has become the ultimate design toolkit for Mac OS. Why so many people prefer it over Photoshop? The answer is surprisingly simple – Sketch limits it's user expressiveness less than Photoshop. It allows you to create reusable design elements and then bulk-update their parameters, just like Sass, but in an interactive, WYSIWYG environment. There are many other ways to further improve the designer's experience. Watch another talk from Brett Victor, [Drawing Dynamic Visualizations](https://vimeo.com/66085662), for further inspiration.


## The curse of DSLs

If we know the very basic principles for a perfect domain specific language, why the available domain specific tools not yet there? Why are we not living in an unlimited WYSIWYG world?

While domain specific languages deliver an unparalleled way to manipulate and understand data, they also quietly smuggle spoiled software design patterns. The existence of many, small DSLs which cannot speak with each other leads in a long perspective to a dysfunctional, fragmented software world.

In real world, there is a constant cooperation between domains. Image manipulation is often used for the needs of machine learning and bioinformatics, which in turn increasingly become an important tool for architecture and vehicle design. The rapid IoT development results in smaller and more autonomous devices, which opens a new world for early disease detection, health monitoring systems or intelligent cities.

However there is hardly any cooperation in the software world. Software developers are writing the same code over and over again, which leads to high development costs and innovation stagnation. You cannot just take a shape editor from your favorite graphics software, fine tune it for your needs, glue with machine learning tools and create an AI-assisted 3D modelling tool for the needs of 3D printing. Instead of hours you currently need days or months to accomplish such task. Even if you find libraries that implement similar functionality, an enormous amount of work has to be done before it will follow the "no limits" principle and provide a truly flexible environment, so your users could fine tune how the model is build. As a result, instead of improving existing components or inventing new ways of manipulating data, developers re-implements known solutions from scratch in every new application. 


## Luna, the language

The guidelines for domain specific languages to follow the first principle are clear. In order to deliver the immediate connection between people and their creation, domain specific languages need to combine rich data visualization and intuitive data manipulation in a single, smooth experience. There is however no rule of thumb how to do it correctly. It strongly depends on the particular domain and the user's preferences, which makes the second paradigm, ability to customize components, even more important.

Following the second principle, however, is more tricky. How can we design a language and be sure it does not limit people's expressiveness? How can we allow users to both create custom reusable components and deeply modify existing ones yet keep the interface simple and don't require them to be programmers? The idea is to allow the user to incrementally change the perspective. Instead of resorting to an underlying programming language, we can allow to literally dive into every component and use the same (or very similar) language to describe how the sub-components communicate. Diving further into nested components allows users to gradually proceed from high to low levels of abstraction on demand.

This is exactly what Luna does. It was built upon three main concepts:


* **Data visualization and manipulation environment**<span class="uiref">1</span>  
  From the highest perspective, Luna allows you to visualize and manipulate data using interactive and extensible WYSIWYG components. Moreover, Luna provides a way to easily define new components, modify existing ones and share them with the community.

* **Data flow graph**<span class="uiref">2</span>  
  You can literally zoom out to see how the high-level components are wired together forming a data flow graph. You can rewire them or insert new components to redefine how the graph works. Luna delivers components which spread over all levels of abstraction, from high to low. From painting canvas over statistical functions to bitwise operators

* **Nested data flow graphs and code representation**<span class="uiref">3</span>  
  Every component in Luna is built out of other components, without exception. You can always dive all the way down to the desired level of abstraction and fine tune it to your needs. You can also collapse several connected components into new, more powerful one and share it with others. Moreover, Luna provides it's users with a very unique capability to switch between representations – from the data flow graph to code and vice versa. It implies a very important truth – the graph is as powerful as the code.

![](/assets/placeholder.jpg)


Luna was designed as an unified environment for building and hosting visually rich domain specific languages. It blurs the boundaries between domains, allowing tools from different fields to seamlessly communicate and coexist. 



## Additional resources

There are several articles and videos which would help you better understand the core concepts behind Luna. We strongly encourage you to read and watch them:

* [Inventing on Principle](https://vimeo.com/36579366)
* [Drawing Dynamic Visualizations by Brett Victor](https://vimeo.com/66085662)
* [The Coming Software Apocalypse](https://www.theatlantic.com/technology/archive/2017/09/saving-the-world-from-code/540393/)




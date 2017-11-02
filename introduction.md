
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

While domain specific languages deliver an unparalleled way to manipulate and understand data, they quietly smuggle spoiled software design patterns. The existence of many, small DSLs which cannot speak with each other leads to a dysfunctional, fragmented software world in a long perspective.

In real world, there is a constant cooperation between domains. Image manipulation is often used for the needs of machine learning and bioinformatics, which in turn increasingly become an important tool for architecture and vehicle design. The rapid IoT development results in smaller and more autonomous devices, which opens a new world for early disease detection, health monitoring systems or intelligent cities.

However there is hardly any cooperation in the software world. Software developers are writing the same code over and over again, which leads to high development costs and innovation stagnation. You cannot just take a shape editor from your favorite graphics software, fine tune it for your needs, glue with machine learning tools and create an AI-assisted 3D modelling tool for the needs of 3D printing. Instead of hours you currently need days or months to accomplish such task. Even if you find libraries that implement similar functionality, an enormous amount of work has to be done before it will follow the "no limits" principle and provide a truly flexible environment, so your users could fine tune how the model is build. As a result, instead of improving existing components or inventing new ways of manipulating data, developers re-implements known solutions from scratch in every new application. 


unparalleled
## Luna, the language



 The answer is obvious. Creating a language that follows these principles is a very complex and time-consuming process. Each domain is different. There is no universal guide how a language should look like, so designing and testing new tools, visualizations or interaction ideas is the only way to get the perfect combination. Moreover, every idea requires a significant development time before it could be tested, so either you or your team need a solid software development background.


Luna was designed to 


Luna was designed to make it easy to create any embedded DSL with a rich syntax in it.


  having the same powers developers currently do and using them in an instant? The answer turns out to be simple as well. Creating a language that follows these principles is a very complex and time-consuming process. Each domain is different. There is no universal guide how a language should look like, so designing and testing new tools, visualizations or interaction ideas is the only way to get the perfect combination. Moreover, every idea requires a significant development time before it could be tested, so either you or your team need a solid software development background.


We are living in a world of hundreds of small, very limited, domain specific languages. They are hardly extendable and cannot speak with each other easily. 
  
TODO below this line
= = = = = = = = = = = = = = = = = = = =


You cannot borrow an animation editor from your favorite video editing software and just paste it into your new graphic design application. Even if you find libraries that implement such functionality, an enormous amount of work has to be done before it will the "no limits" principle. Your users should be able to create custom animation curves, parametrize them with earlier computed values

Let's imagine a simple example. You want to add an animation editor to your graphic design application, so your users could not only create shapes but also see them moving. You cannot borrow it from your favorite graphic software so you have to either develop it from scratch or use some library that implements it.

for example building software, animation module – timeline – from scratch.

There are appear to be two main reasons among various domains. First, we are constantly searching for the perfect language for a particular domain. Second, creating a well-designed language is very hard and time-consuming.

Luna was built on top of principles described above – "instant feedback loop" and "no limits".


It is very important to understand, that logically there is no difference between drawing a rectangle in a graphic

{domain...} = data flow = software creation

You can think about Luna from three perspectives:

* **Code**
From the most low-level perspective, Luna is a well designed, functional programming language with its own textual syntax representation. You can write Luna code and compile it to executables just like in any other programming language.
* **Data flow graph**
From the higher perspective, Luna is a data flow modeling language with a whiteboard-like interface. You can literally draw how data flows between components.
* **Data visualization and manipulation environment**
From the highest perspective, Luna allows you to display and manipulate data in a WYSIWYG fashion.

It's completely extensible, so supporting new data is as simple as creating

Luna was designed to be the ultimate backbone for any modern domain specific language. You can think about it like about a meta-language. Luna is a language itself, but it is easily extendable

meta-language, a language that can easily
Luna unifies the domains, tools




## Additional resources

There are several articles and videos which would help you better understand the core concepts behind Luna. We strongly encourage you to read and watch them:

* [Inventing on Principle](https://vimeo.com/36579366)
* [Drawing Dynamic Visualizations by Brett Victor](https://vimeo.com/66085662)
* [The Coming Software Apocalypse](https://www.theatlantic.com/technology/archive/2017/09/saving-the-world-from-code/540393/)




xxxxxx


When working on



Luna Language is
an open source, WYSIWYG data processing language. It was

Luna is an open source, WYSIWYG data processing, and visualization environment. Its goal is to redefine the way people are able to gather, understand and manipulate data. Luna targets domains where data processing is the primary focus, including data science, bioinformatics, graphic design, architecture, IOT development, machine learning or microservices integration. Each such domain requires a highly tailored data processing toolbox. Luna provides both a solid foundation for building such toolboxes as well as growing library of existing ones. At its core, Luna delivers a powerful, data-flow modeling language, called the Luna Language and an extensive data visualization and manipulation framework, called the Luna Studio.



Luna was designed to be the ultimate backbone for any domain-specific WYSIWYG languages.









While choosing the technology stack, developers are afraid of any closed technology, because it will cause their headache sooner than later.

Any violation of this rule leads to a solution, which


They drastically lower the learning curve, despite they boost they are very limited in comparison to programming languages



---





But, is it always better than writing code? Is it more expressive? Arguably. While digital canvas, like Photoshop, allows manipulating elements in a WYSIWYG way, it lacks a parametric expressivity delivered for example by HTML, SVG and CSS. Let's think about a website design. There are five, evenly arranged items in the menu bar. If you want to add a new item and change the color palette of the website, all you have to do is to change a single line in HTML and a color declaration in CSS. No matter how complex the website is, every element will update automatically. Doing the same in Photoshop requires an order of magnitude more time – create a new menu item, use an alignment tool to arrange the elements, manually change the colors and probably re-apply some filters in more complex website areas. However, using HTML, SVG and CSS within a text editor to express an artistic vision would hardly be possible because it alienates you from your real creation and breaks the instant feedback loop. So would it be possible to invent a better design language than Photoshop or combination of CSS, SVG and HTML? Definitely.

#### Language principles

What is a good language? What are the principles it has to follow to become the ultimate communication tool in a particular domain?

A good example are visual programming languages, allowing processing data by connecting high level, visual components together. People feel limited regarding what they are able to create by connecting predefined, high-level components. Even if these components could be extended by writing code, the approach feels incomplete and broken by design. Developers prefer generic solutions, while domain experts often cannot write code at all.

A good example are visual programming languages. Despite their ability to clearly visualize the software structure, they limit

In contrast to text-based programming languages, almost every visual programming language is limited to a set of high-level components.

Even if users can create custom components by using some low-level API, they tend to reject such solutions because

instant feedback loop + no limits


Any limitation in a languages expressiveness violates peoples freedom to express thoughts. Even in a very narrow domain-specific use cases,

Even if places its user in a closed world Developers feel limited by what they are able to express by connecting predefined elements. Even if these elements could be extended by writing code, the approach feels incomplete and broken by design. If you need sometimes to escape to another language to fix its pains,

If a language requires you to use other, more expressive languages to

Even if visual programming brings some important values, like better software architecture visualization, developers

its possibilities. If a languages expressiveness is limited by any boundaries, it will affect Vast majority of domain specific tools violate this principle. Almost every

Any violation of these principles leads to
has its own principles, however there is one that we believe is the foundation for all , one such principle is that creators need an
The most important rule such language has to follow is to keep the user in an instant feedback loop. Every violation of this rule

There are two great talks from Brett Victor, a human-computer interaction visonary, exactly about this topic. You should watch them now:

* [Inventing on Principle](https://vimeo.com/36579366)
* [Drawing Dynamic Visualizations](https://vimeo.com/66085662)

It doesn't mean however, that it is the best possible language for this particular domain. Would creating graphics by writing code be so expressive as with digital canvas? Definitely not, otherwise the majority of designers would have been writing code already! So could creating graphics be more expressive than nowadays? Definitely.

layers -&gt; nodes -&gt; simple color dependencies -&gt; possible in code, not in photoshop. Unified base for languages

This is the exact reason why so many new domain specific programming languages appear every year in the software world. Every domain is constantly looking for the most expressive communication language.

A language is the tool to form our thoughts, to understand each other, to communicate.

Communication is the ability to express thoughts as receive feedback information. Language is the tool for encoding and decoding the information. A good language allows expressing thoughts in a concise, fast and understandable way. A good language is "expressive". There is nothing more important than expressiveness when you're solving a problem, searching for a new solution, testing and playing with different options. No matter if you are examining drug effects while searching for a new treatment, designing a complex building shape or developing new IOT device, the speed of testing new ideas is the crucial factor for your success. Faster iterating allow you to test wider range of parameters including those that should not work at first glance. Thus, expressiveness directly affects not only the total time needed to solve a problem in an exponential way, it often is the key to find the solution at all.

Communication is both expressing thoughts as well as receiving feedback information. A tool for encoding and decoding thoughts is called a language. A good language allows expressing thoughts in a concise, fast and understandable way. A good language is "expressive". There is nothing more important than expressiveness when you're solving a problem, searching for solution, testing and playing with different options. No matter if you are examining drug effects while searching for a new treatment, designing a complex building shape or developing new IOT device, the speed of testing new ideas is the crucial factor for your success. Faster iterating allow you to test wider range of parameters including those that should not work at first glance. Thus, expressiveness directly affects not only the total time needed to solve a problem in an exponential way, it often is the key to find the solution at all.

This is the exact reason why so many new domain specific programming languages and appear every year in the software world.




unparalleled
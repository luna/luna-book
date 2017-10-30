

# What is Luna?


Luna is an open source, [WYSIWYG](https://en.wikipedia.org/wiki/WYSIWYG) data flow modeling language. Its goal is to redefine the way people are able to gather, understand and manipulate data. 

Luna targets domains where data processing is the primary focus, including data science, bioinformatics, graphic design, architecture, IOT development, machine learning or microservices integration. Each such domain requires a highly tailored data processing toolbox. Luna provides both a solid foundation for building such toolboxes as well as growing library of existing ones. At its core Luna delivers a powerful, visual data-flow editor and an extensive data visualization and manipulation framework.

Let's start with a question. What does it mean that Luna is a "language"? Is it like English? Is it like a programming language? I would say neither. It's something with a much broader concept. In this chapter I will try to guide you trough Luna foundations and show you the full picture of what Luna was designed for.

![](/assets/screen1.png)


## Language, the foundation of communication.

> **The limits of my language are the limits of my world.**
 
Communication is a process of exchanging information. It requires a language to formulate the information and a medium to store and transfer it. A well designed language should empower people with the ability to both express their thoughts in a rapid and concise way as well as understand the feedback response easily. It is especially important with research, because it directly affects how fast you can iterate – test new ideas and understand intermediate results. Fast iterations make it possible to test wider range of parameters including those that should not work at first glance, allowing you to much better understand the domain you are investigating. Thus the language design directly affects not only the total time needed to solve a problem in a non-linear way, it often is the key to find the solution at all. No matter if you are examining drug effects while searching for a new treatment, designing a complex building shape or developing new IOT device, the speed of testing new ideas is the crucial factor for your success.


#### Language design principles

There is no silver bullet language. Every domain is characterized by a set of distinct assumptions and requires highly tailored communication language. Such language often does not even remind a spoken one. English is great for everyday conversations. However, it would be a horrible choice as music or mathematical notations replacement. 

The language design depends heavily on the available medium as well. The most common language used by designers nowadays is a digital canvas and an associated toolbox of layers, brushes, shapes, filters, etc. It allows expressing thoughts in a much more flexible and universal way than pen and paper, providing the same level of interactivity and instant feedback loop.

So what is a good language? What are the principles it has to follow to become the ultimate communication tool in a particular domain? We believe there are two basic principles, every domain specific language has to follow.

* **People need an immediate connection to what they are making**
This principle was first publicly introduced by Brett Victor, a human-computer interaction visonary, during his talk [Inventing on Principle](https://vimeo.com/36579366). You should definitively see it to better understand the concepts behind Luna. Any violation of this principle alienates the user from the actual problems he is trying to solve, which consequently decreases the understanding and increases the number of mistakes. 

* **People cannot be limited by the language they are using**
People tend to reject any language which obviously limits their expressiveness. This is the exact reason why so many WYSIWYG solutions never catch up. Website creators, game creators or visual programming languages provide their users with a limited set of predefined, high level components. Even if these components can be extended by writing code, the need to resort to some underlying programming language spoils the design and makes it unusable for a less technical audience.

#### Principle violation

Violation of any of these rules always leads to a sub-optimal solution. Let's consider the graphic design again. Is using Photoshop always better than writing HTML, Sass and JavaScript code? Arguably. These solutions violate the first and the second principle respectively. Photoshop provides a WYSIWYG digital canvas with predefined, hardly extendable set of tools. HTML, Sass and JavaScript on the other hand, provide a text interface and thus alienate the user from its real creation, but do not set tight restriction on the expressiveness. Let's consider two use cases:

* A website design. There are five, evenly arranged items in the menu bar. If you want to add a new item and change the color palette of the website, all you have to do is to modify a single line in HTML and a color variable in Sass. No matter how complex the website is, every element will update automatically. Doing the same in Photoshop requires an order of magnitude more time – create a new menu item, use an alignment tool to arrange the elements, manually change the colors and probably re-apply some transformations and filters in more complex website areas. 

* An artistic painting. Using HTML, SVG and Sass within a text editor to express an artistic vision would hardly be possible. The more creative and discoverable the process is, the more important the instant feedback loop becomes. 

An important question emerges – would it be possible to fuse both approaches? It's not only possible. There are already solutions heading in the right direction. Think about Sketch, which has become the ultimate design toolkit for Mac OS. Why so many people prefer it over Photoshop? The answer is surprisingly simple – Sketch limits it's user expressiveness less then Photoshop. It allows you to create reusable design elements and then bulk-update their parameters, just like Sass, but in a WYSIWYG environment. There are however many ways to further improve the designers toolbox. Watch another talk from Brett Victors [Drawing Dynamic Visualizations](https://vimeo.com/66085662) for further inspiration.


## Luna, the language

If we know the very basic principles for a perfect domain specific language, why the available tools for graphics, architecture, electronic design, music creation or software building are not yet there? Why are we not living in a WYSIWYG world, having the same powers developers currently do and using them in an instant ? The answer turns out to be simple as well. Creating a language that follows these principles is a very complex and time consuming process. Each domain is different. There is no universal guide how a language should look like, so designing and testing new tools, visualizations or interaction ideas is the only way to get the perfect combination. Moreover, every idea requires a significant development time before it could be tested, so either you or your team need a solid software development background. 

You cannot borrow an animation editor from your favorite video editing software and just paste it into your new graphic design application. Even if you find libraries that implement such functionality, an enormous amount of work has to be done before it will the "no limits" principle. Your users should be able to create custom animation curves, parametrize them with with earlier computed values  

Let's imagine a simple example. You want to add an animation editor to your graphic design application, so your users could not only create shapes but also see them moving. You cannot borrow it from your favorite graphic software so you have to either develop it from scratch or use some library that implements it.

for example building software , animation module – timeline – from scratch. 

There are appear to be two main reasons among various domains. First, we are constantly searching for the perfect language for a particular domain. Second, creating a well designed language is very hard and time consuming.  

Luna was build on top of principles described above – "instant feedback loop" and "no limits".


Luna was designed to be the ultimate backbone for any modern domain specific language. You can think about it like about a meta-language. Luna is a language itself, but it is easily extendable 

meta-language, a language that can easily 
Luna unifies the domains, tools




When working on 



Luna Language is
 an open source, WYSIWYG data processing language. It was 

Luna is an open source, WYSIWYG data processing and visualization environment. Its goal is to redefine the way people are able to gather, understand and manipulate data. Luna targets domains where data processing is the primary focus, including data science, bioinformatics, graphic design, architecture, IOT development, machine learning or microservices integration. Each such domain requires a highly tailored data processing toolbox. Luna provides both a solid foundation for building such toolboxes as well as growing library of existing ones. At its core, Luna delivers a powerful, data-flow modeling language, called the Luna Language and an extensive data visualization and manipulation framework, called the Luna Studio.



Luna was designed to be the ultimate backbone for any domain specific WYSIWYG languages.









While choosing the technology stack, developers are afraid of any closed technology, because it will cause their headache sooner than later.

Any violation of this rule leads to a solution, which 


   They drastically lower the learning curve,  despite they boost they are very limited in comparison to programming languages



---





  But, is it always better than writing code? Is it more expressive? Arguably. While digital canvas, like Photoshop, allows manipulating elements in a WYSIWYG way, it lacks a parametric expressivity delivered for example by HTML, SVG and CSS. Let's think about a website design. There are five, evenly arranged items in the menu bar. If you want to add a new item and change the color palette of the website, all you have to do is to change a single line in HTML and a color declaration in CSS. No matter how complex the website is, every element will update automatically. Doing the same in Photoshop requires an order of magnitude more time – create a new menu item, use an alignment tool to arrange the elements, manually change the colors and probably re-apply some filters in more complex website areas. However, using HTML, SVG and CSS within a text editor to express an artistic vision would hardly be possible because it alienates you from your real creation and breaks the instant feedback loop. So would it be possible to invent a better design language than Photoshop or combination of CSS, SVG nd HTML? Definitely.

#### Language principles

What is a good language? What are the principles it has to follow to become the ultimate communication tool in a particular domain? 

A good example are visual programming languages, allowing processing data by connecting high level, visual components together. People feel limited regarding what they are able to create by connecting predefined, high-level components. Even if these components could be extended by writing code, the approach feels incomplete and broken by design. Developers prefer generic solutions, while domain experts often cannot write code at all.

A good example are visual programming languages. Despite their ability to clearly visualize the software structure, they limit

In contrast to text-based programming languages, almost every visual programming language is limited to a set of high-level components. 

Even if users can create custom components by using some low-level API, they tend to reject such solutions because 

instant feedback loop + no limits 


Any limitation in a languages expressiveness violates peoples freedom to express thoughts. Even in a very narrow domain specific use cases,  

 Even if  places its user in a closed world  Developers feel limited by what they are able to express by connecting predefined elements. Even if these elements could be extended by writing code, the approach feels incomplete and broken by design. If you need sometimes to escape to other language to fix it's pains,  

If a language requires you to use other, more expressive languages to 

Even if visual programming brings some important values, like better software architecture visualization, developers 

  its possibilites. If a languages expressiveness is limited by any boundaries, it will affect  Vast majority of domain specific tools violate this principle. Almost every 

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


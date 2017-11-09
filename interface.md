# Interface

We are ready to get started! If you're the kind of person who just skips introductions, you might want to read it anyway because it explains what you need to follow this chapter.


## Dashboard

![](/assets/hello_screen.png)

Alright, you've got Luna Studio installed and running on your computer. After launch you will be greeted with the Dashboard <span class="uiref">1</span>. Think about it like about a mix of a "hello screen" and a place gathering all common quick start actions. You can always access the dashboard simply by pressing the Luna logo on the left toolbar (<comingsoon>coming soon</comingsoon>) <span class="uiref">2</span> (or by selecting it from menu `View → Dashboard`).

Moreover, if this is your first Luna Studio execution, you will be facing an interactive welcome tutorial. You can always start it again right from your dashboard <span class="uiref">3</span>. 

Dashboard allows you to:
  * <span class="uiref">4</span> access the community channels (forum and chat);
  * <span class="uiref">5</span> load one of example projects;
  * <span class="uiref">6</span> create new local project; 
  * <span class="uiref">7</span> open your recent projects;
  * <span class="uiref">8</span> load one of community projects;
  * <span class="uiref">9</span> create a new community project. 



## Workspace

![](/assets/workspace.jpg)

Luna is like a toolbox. The Workspace is a way to arrange the tools for your convenience. The Workspace is divided into panels<span class="uiref">1</span> containing tabs. Each tab is a separate tool from the toolbox. The most important tools are described below.

#### Luna Visual Editor
Luna Visual Editor <span class="uiref">2</span> delivers a whiteboard-like interface for editing data flow graphs. Moreover, it seamlessly integrates other tools from the toolbox. For example, the Visual Editor is able to display interactive results visualizations next to nodes, giving you instant feedback right in the place where you are processing the data.

#### Code Editor
Code Editor <span class="uiref">3</span> is a powerful text editor. It allows you to edit the textual Luna representation and source code of other languages. It is integrated with the Visual Editor – whenever you modify the code, the data flow graph updates. It works the other way around too – every graph modification updates the code.

#### Data View <comingsoon>coming soon</comingsoon>
Data View <span class="uiref">4</span> is a data visualization and manipulation toolkit. It provides processing utilities highly tailored for a particular data type. You can switch between available visualizations and manipulators or [define your own](dummy.md). Note that in the current release, the Data View is available only within the Visual Editor. It would be available as separate tool soon.

#### Project view
Project View <span class="uiref">5</span>is a list of modules in current Luna project. You will learn more about modules in the [Modules and libraries](dummy.md) chapter.

#### Status bar
Status bar has two important properties: 
* Controlling the graph evaluation engine<span class="uiref">6</span>. By default Luna tries to evaluate every node as soon as possible. There are sometimes situations, however, when you want to disable this behavior and refresh the scene on demand. The pause button allows stopping and resuming the interactive graph evaluation. The refresh button tells Luna to re-compute every value from scratch.
* Current status information <span class="uiref">7</span> displays information about what is currently computed and guides you when using tools. Currently however, the information is very limited.

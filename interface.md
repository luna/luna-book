# Interface

We are ready to get started! If you're the kind of person who just skips introductions, you might want to read it anyway because it explains what you need to follow this chapter.


## Dashboard

![](/assets/hello_screen.png)

Alright, you've got Luna Studio installed and running on your computer. After launch you will be greeted with the Dashboard. Think about it like about a mix of a "hello screen" and a place gathering all common quick start actions. You can always access the dashboard simply by pressing the Luna logo on the left toolbar.

Dashboard allows you to:
  * access the community channels (forum and chat);
  * load one of example projects or tutorials;
  * create new local project; 
  * open your recent projects;
  * load one of community projects;
  * create a new community project. 


## Workspace

![](/assets/workspace.png)

Luna is like a toolbox. The Workspace is a way to arrange the tools for your convenience. The Workspace is divided into panels containing tabs. Each panel is a separate tool from the toolbox. The most important tools are described below.

#### Luna toolbar

This pane contains the most common actions concerning Luna Studio, like:

  * <span class="uiref">1</span> accessing the dashboard;
  * <span class="uiref">2</span> creating new modules;
  * <span class="uiref">3</span> searching the modules in the current project.

#### Luna Visual Editor
Luna Visual Editor <span class="uiref">4</span> delivers a whiteboard-like interface for editing data flow graphs. Moreover, it seamlessly integrates other tools from the toolbox. For example, the Visual Editor is able to display interactive results visualizations next to nodes, giving you instant feedback right where you are processing the data.

#### Code Editor
Code Editor <span class="uiref">5</span> is a powerful text editor. It allows you to edit the textual Luna representation and source code of other languages. It is integrated with the Visual Editor – whenever you modify the code, the data flow graph updates. It works the other way around too – every graph modification updates the code.

#### Project view
Project View <span class="uiref">6</span> is a list of modules in current Luna project.

#### Status bar
Status bar has two important properties: 
* Controlling the graph evaluation engine <span class="uiref">7</span>. By default Luna tries to evaluate every node as soon as possible. There are sometimes situations, however, when you want to disable this behavior and refresh the scene on demand. The pause button allows stopping and resuming the interactive graph evaluation. The refresh button tells Luna to re-compute every value from scratch.
* Current status information <span class="uiref">8</span> displays information about what is currently computed and guides you when using tools. Currently, however, the information is very limited.

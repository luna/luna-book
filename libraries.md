# Using and creating libraries

> **[info] Changes ahead!**
>
> This describes the simplest way to share libraries, introduced in Luna Studio 1.3 beta. A proper package manager is currently being designed and coded and will be available soon.

## What is a library?

Library is a set of modules shared by others for reuse in other projects. This is the base way to share code between different projects – every functionality such as a database driver, a set of image processing functions or an awesome data science toolkit constitutes a library.

## How to create a library?

On the technical level library does not differ at all from an ordinary Luna project. It has the same structure as any other project. Maybe even some of the projects you've already created deserve to become publicly available libraries?

From the design perspective, there are some things you need take into account when creating a library. In order for others to enjoy using it, put some thought into the basic usage patterns – what set of functionalities is really needed and how do the functionalities compose? Think about the classes you define – do they encompass well the usage you intend for the library?
If yes – congratulations, your project is a library! Publish it and encourage others to use it. Also, let us know, we love to learn about awesome things happening in the community!

## How to use a library?

The basic flow (before proper package management comes to Luna) is just to put it in the `local_libs` directory in your Luna project. After that, it will be available for other modules to import. Note that the name of the library is the first part of module name. It's probably best to explain it with an example. Suppose you have the following directory structure:
```
MyProject/
  MyProject.lunaproject
  src/
    Main.luna
  local_libs/
    MyLib/
      MyLib.lunaproject
      src/
        Foo.luna
        Bar.luna
```

And `Bar.luna` file is just:

```
def barify t: 'bar ' + t.toText + ' bar'
```
Then, you can import the `MyLib.Bar` module inside `Main.luna` (also inside `Foo.luna` – any module is available throughout the library defining it). So now your `Main.luna` file may look like this:

```
import Std.Time
import MyLib.Bar

def main:
    barify Time.now
```
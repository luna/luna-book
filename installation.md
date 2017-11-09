## What you need to dive in

Luna is available as a stand-alone application for Mac OS, Linux and Windows named Luna Studio. All its core graphical tools are based on web technologies, so it is possible to run them in a web browser too. However, Luna Studio desktop distribution was tightly integrated with [GitHub's Atom](https://atom.io) in order to provide decent code editing capabilities. Currently only the desktop distribution is supported, however, you are welcome to play and [contribute](http://luna-lang.org/contribute) to the web version. To learn more, please refer to the [Luna architecture description](architecture.md).

#### Luna Manager

The Luna Manager is a tool for managing your Luna environment. It allows installing and uninstalling different Luna versions side by side, switching between them, managing the development environment, building Luna packages and much more. It is bundled with a simple graphical interface for everyday use, like installing or updating Luna.

For your convenience we distribute it as a binary, so you can download it and literally "double click" to start the installation process. You can download it from our [website](http://luna-lang.org) or build it from [source](http://github.com/luna/luna-manager).

![](/assets/placeholder.jpg)

After running the installer you can choose whether you want Luna to be installed locally \(recommended option\) or system-wide. If you need more fine grained control over the installation process, please download and use the Luna Command Line Manager from our [website](http://luna-lang.org) instead.

> **\[info\] Local or system-wide installation?**
>
> Local installation has many advantages over system-wide one – it does not require the administrator password, is more modular and you can literally remove the installation directory to completely uninstall Luna or move it to other machine keeping all your settings. We recommend it for everyone, unless you've got important reasons to install it globally. A good reason is when the system is shared among many users and you want to minimize the amount of used disk space.

After the successful installation you should be able to execute Luna Studio using your system application manager \(like Mac OS Spotlight, Gnome Shell or Windows Start menu\) or run it manually from the installation path \(`$HOME/.luna` in case of local installation\).


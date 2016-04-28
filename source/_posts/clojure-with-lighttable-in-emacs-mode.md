title: Clojure with Light Table and Emacs keybindings
date: 2015-01-03 14:08:38
categories: clojure
tags: 
- clojure
- dev-tools
- lighttable 
---

 {% img img-thumbnail http://www.lighttable.com/images/logo.png %}

  When I [teach people Clojure](http://clojure.practical.li) I use [Light Table](http://lighttable.com/) because it is really simple to use and its _Instarepl_ gives instant feedback of the code as you type it.  This feedback helps you understand Clojure quickly and gives you more confidence when coding.
  
  As I do most of my Clojure development (and most everything else) in [Emacs](http://www.gnu.org/software/emacs/) I really miss the excellent Emacs keybindings when I use Light Table.  Luckily there is an [Emacs plugin for Light Table](https://github.com/LightTable/Emacs), so here is a quick guide on how to install & use this Emacs plugin.

<!-- more -->

#### Install Emacs plugin for Light Table

  Light Table has many plugins available and the easiest way to install them is with the plugin manager.  In Light Table, open the command bar with `Ctrl-Space` (`Cmd-Space` on MacOSX) and type `plugin`

  Select the plugin manager and a new window opens, listing all the currently installed plugins.  Select the `available` tab in this window.  
  
  There are many plugins, so type `emacs` to quickly find the plugin.  Then select `install` on the Emacs plugin
  
![Light Table plugin manager - Emacs install](/images/lighttable-plugins-emacs-install.png)

  At the time of writing, installing this plugin generates a warning message due to a format change in Light Table 0.7.0.  The plugin still works correctly however.

![Light Table Emacs plugin - warning message](/images/lighttable-plugins-emacs-install-error-vector-map.png)


#### Add Emacs plugin to Light Table user.behavior 

  Finally, we need to edit the Light Table user behaviours to use the Emacs keybindings with the editor.
  
  Open the command bar with `Ctrl-Space` (`Cmd-Space` on MacOSX) and type `behavior`, selecting on the `Settings: user Behaviours` command.
  
  In the user behaviours window that opens, edit the configuration by adding the following line to the `editor` section
  
    [:editor :lt.plugins.emacs/activate-emacs]

  The user behaviors configuration should look something like this:
  
![Light Table user behaviors configuration - Emacs activate](/images/lighttable-plugins-emacs-behaviors-user-editor-emacs-activate.png)

> The format of user.behaviour has changed from Light Table version 0.7.0 onwards.  Configuration is now defined using vectors or maps, rather than lists as before.  At the time of writing, the configuration line on the Github repository README.md is incorrect (a [pull request](https://github.com/LightTable/Emacs/pull/25) has been created).


#### Using Emacs keybindings with Light Table

  The Emacs keybindings seem to be exactly what you would expect in Emacs.  Obviously there are a few differences between the design of Light Table and Emacs, although conceptually things seem to work the same.
  
  Here are a few keybindings that may not be immediately obvious:

`Alt-x` - opens the command bar so you can find the command you want by typing - in the same way as you use `meta-x` in Emacs.

`C-x f` - open a file using the system file manager (Ctrl-Shift-o in Light Table default keybinding)

`C-x C-f` - select a file from those added to the Light Table workspace - the Light Table `Navigate: Open Navigate` command is called.

`C-x o` - switch to next window tab on the right - similar to the next buffer window in Emacs.

`C-x k` - close the current tab - similar to killing a buffer, but without a choice.

`Alt-g g` - go to line.

`C-x h` - select all.

`C-x C-e` - evaluate all the code in the current tab.

  You can see all the Emacs keybindings at the [Emacs Plugin Github repository](https://github.com/LightTable/Emacs/blob/master/emacs.keymap).

  Have fun with Light Table and Emacs keybindings.  If you have any modifications of the Emacs keybindings you find useful, please share them in the comments.
  
Thank you.
[@jr0cket](https://twitter.com/jr0cket)

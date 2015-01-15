title: tweaking light table for a great clojure experience
date: 2015-01-03 22:27:09
categories: dev-tools
tags:
- lighttable
- clojure 
- git
---

{% img img-thumbnail /images/lighttable-logo.png %}

  [Light Table](http://lighttable.com) provides a great development environment for Clojure, ClojureScript & JavaScript.  With a few tweaks and some of the many plugins you can make Light Table do even more.  Here are a few of the tweaks and plugins I use for my development with Light Table.

<!-- more -->

#### Ubuntu Fonts 

  The [Ubuntu fonts](http://font.ubuntu.com/) are very clear and easy on the eyes, so are great for coding with.  I use the Ubuntu Mono font for all my editors by adding the following line to my user behaviors

  Open the command panel in Light Table with `Ctrl-Space` and type `user behaviors`.  Then edit the file that opens and add the following line
  
```clojure
    [:editor :lt.objs.style/font-settings "Ubuntu Mono" 16 1.2]
```

  When I run workshops or other demos I increase the font size to 20, to make the code easier to read from a distance.

```clojure  
    [:editor :lt.objs.style/font-settings "Ubuntu Mono" 20 1.2]
```

> You can use Ubuntu Fonts with operating systems other than Ubuntu by downloading the fonts from [font.ubuntu.com](http://font.ubuntu.com/)

#### Themes

  The default theme for Light Table is pretty good, however my prefered Light Table font is called _Tommorow Night_ and I configure my user behaviors to use this theme by adding the following line:

```clojure
    [:editor :lt.objs.style/set-theme "tomorrow-night"]
```

> There is also an Ubuntu theme plugin that I have just spotted, so I am trying that out although I want to tweak some of the colours before I make the switch.

#### Bracket fun 

From Light Table 0.7.0 onwards parens are not auto-closed anymore, so when you type `(` then you have to also type `)`.  Coming from Emacs, I find this limiting, so luckily you can add this behaviour back in by editing your user behaviors.  

```clojure
    [:app :lt.objs.settings/pair-keymap-diffs]
```

#### Emacs keybindings 

  The Emacs plugin is a wrapper around the Code Mirror keybindings for Emacs.  Installing the Emacs plugin with give you many of the Emacs keybindings you enjoy and you can easily customise them by changing the keybindings mapping in the plugin.
  
  See my previous post on how to use the [Emacs plugin with Light Table](http://localhost:4004/2015/01/clojure-with-lighttable-in-emacs-mode.html). 

#### Git Status Bar

  The Git status bar plugin simply indicates the Git branch your current editors' file is in, assuming it is under version control.

{% img img-code /images/lighttable-plugin-git-status-bar.png %}
  
  Install using the plugin manager and restart Light Table (you may just be able to select "Reload App Behaviours" from the Light Table commands).  Then open a file under version control and you will see its Git branch in the right corner of the status bar (the bar at the bottom of Light Table).

> Git branch / status will only show for files that are in repositories whose root is in your workspace.

#### Gitlight 

  Gitlight plugin provides a visual Git client that can stage and commit changes, push & pull changes with remote repositories and show visual diffs of changes.  Install Gitlight from the Light Table plugin manager and restart Light Table (you may just be able to select "Reload App Behaviours" from the Light Table commands).

  Use Gitlight by opening the command panel and type `gitlight`, you will see a list of available commands

{% img img-code /images/lighttable-gitlight-commands.png %}

  If you open a file from a project managed by git you can see the status of all the files in that project using the command `gitlight-status`

{% img img-code /images/lighttable-gitlight-status-window.png %}  
  
  If you select diff for any of the files in the project, you get a nice visual comparison of the changes between what is committed and your working copy.
  
{% img img-code /images/lighttable-gitlight-diff-visual.png %}    

#### Modific - show changes since last Git commit

  When you save a file, any changes you made since it was last commited to Git are marked by coloured lines at the left hand side of the editor window, also known as _gutter marks_. 

{% img img-code /images/lighttable-plugin-modific-example.png %}
> modific example with red, green and yellow highlights

* Red    = lines have been deleted  
* Green  = new lines have been added
* Yellow = text that has be modified
  
You can jump between changes using `Ctrl+Shift+PageUp/PageDown`, show the original version by putting the cursor on a changed line and hit `Ctrl+Alt+c` and revert a change by putting the cursor on a changed line and hit `Ctrl+Alt+r`

  Install modific from the Light Table plugin manager and restart Light Table.  Then open a file from workspace project that is under version control.  Now any change you make will be highlighted.


#### Plugins to try next

  There are lots of other plugins I have not tried yet.  Many plugins also provide additional language support.
  
  Here are a few plugins I plan to try next: 
  
* [Slamhound](https://github.com/chadhq/slamhound-lt) - refactor your Clojure namespace
* [howdoi](https://github.com/vgrichina/lt-howdoi) - pull in code solutions from the web
* [recall](https://github.com/joshuafcole/recall) - workspace Persistence 
* [workspace nav](https://github.com/bfabry/workspace-nav) - Navigate the workspace view via the keyboard 

#### Summary

  Light Table provides a lot of great features out of the box, expecially for Clojure, ClojureScript and JavaScript development.  Using tweaks and plugins, Light Table is easy to tailor int a more personalised development experience.

Thank you.
[@jr0cket](https://twitter.com/jr0cket)

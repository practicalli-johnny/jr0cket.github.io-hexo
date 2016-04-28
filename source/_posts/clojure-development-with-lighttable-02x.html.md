title: Clojure development with LightTable 0.2.x
date: 2012-12-04 19:13:00
categories: clojure
tags: 
- clojure
- coding
- dev-tools
- lighttable
---

{% img img-thumbnail http://www.lighttable.com/images/logo.png %}

[LightTable](http://www.lighttable.com/) is a [kickstarter project](http://www.kickstarter.com/projects/ibdknox/light-table) to create new kind of developer tool for Clojure development, inspired by the [Inventing on Principle talk by Bret Victor](http://www.youtube.com/watch?v=PUv66718DII).

LightTable aims to give developers instant feedback about their code, showing how any change affects their applications. Giving you a developer "surface" to work on, which will bring information to the places you need it the most.  The principles of the LightTable design include:

*   Documentation there when you need it, no need to search
*   Edit anywhere and anything - not just text and not just as files
*   Discover by doing, changes produces instantaneous results
*   Shine a light on related pieces of code

<!-- more -->

# Status of the LightTable Project

{% img img-code http://1.bp.blogspot.com/-SU2JlT8A9Kw/UL9Jclni9-I/AAAAAAAAIqc/9ELhASNZrXo/s1600/lighttable-game-example.png %}

LightTable 0.1.x of LightTable showed of  some of the concepts that this tool will eventually have.  It moved away  from the concepts of files and allowed you to work with individual  parts of your code - functions and definitions.

LightTable  0.2.x has fewer concepts implemented than 0.1.0 and may seem like a backward step on the outside.  However the rewrite decision taken for this version allows the team to have a solid code base to bring back all the innovative  features.  This rewrite includes a proper packaging approach making updates become almost transparent, with LightTable grabbing updates behind the scenes and informing you when you need to restart.

{% img img-code http://4.bp.blogspot.com/-9LOuNwvoNE4/UL5RooIZrwI/AAAAAAAAIqA/0xqL_7jufyU/s1600/lighttable-update-notices.png %} 

LightTable still has a long way to go to implement all the ideas it has, but at present it is a usable tool for discovering and developing Clojure code.  In fact it is now at a stage where the team are using LightTable to develop itself, so they are well aware of features that need adding.  There  is quite a list of feature requests over at the [Github Issue tracker for the project](https://github.com/Kodowa/Light-Table-Playground/issues).

{% img img-code http://3.bp.blogspot.com/-te_MuKdFBTQ/TzFLahe2BxI/AAAAAAAAEbY/Bn_JPN_s3qU/s1600/clojure-logo-500x.png %}

# Language support in LightTable
By release time, LightTable will support Clojure, ClojureScript, JavaScript (nodejs) and Python.

Currently LightTable only supports Clojure, but ClojureScript will be the next one to be supported and sounds like its not far away.

# Getting started with LightTable

{% img img-code http://4.bp.blogspot.com/-vgIvECRudu4/UL4AKSsztzI/AAAAAAAAIoc/yNVe3sFkUj8/s1600/lighttable-welcome-screen-update-message.png %}

[Download LightTable](http://lighttable.com/) as
*   a tar file for 32bit or 64bit Linux
*   an app file for MacOSX
*   a zip file for windows

Running LightTable gives you a welcome screen that gives you details of all the keyboard controls.  There are only a few controls to learn, most should be familiar.  You will need to learn these command as LightTable is very keyboard focused, just like Vi and Emacs.

Commands are entered in a small window at the bottom of the screen.  A menu pops up to show you want commands are available, but this is only a guide and you cannot select items on the menu with a mouse. 

# Creating Clojure projects

You can work with Leinignen created Clojure projects, loading exiting ones or creating a new ones.  Or you can fire up the REPL, using Instarepl.

Typically I use Leiningen via the command line to create a new project with the command

    lein new my-project

This allows me to then put the project into version control using Git with the command `git init`

# Working with Projects

Connect allows you to work with a Leiningen projects.

    C-k connect ~/projects/clojure/my-project/src/core.clj

Like with emacs and the Unix command line, LightTable lets you tab through your folder structure to save typing.  Selecting a Clojure file will trigger LightTable to connect to a Clojure REPL environment via Leiningen.  If more than one REPL is running you can choose the project from which the REPL was run.  If no REPL is running you can connect to a leiningen project, which will import all the dependencies and load the namespaces into LightTable.

With a source file you can evaluate directly and the results are displayed on the far right hand side.  These results carry over between all tabs.  This unfortunately can block other code, especially in the Instarepl output.  However, clicking on the output bubbles will get rid of each one.

You can connect to multiple projects within LightTable and when you fire up Instarepl you can decide which one you want to connect to. 

## Using Instarepl

{% img img-code http://4.bp.blogspot.com/-nc5cPfRiLOI/UL5KemAA0DI/AAAAAAAAIpU/AL64k4Ilh1I/s1600/lighttable-instarepl-connect.png %}

This is the REPL environment for LightTable.  It allows you to run any code that LightTable knows about.  Instarepl is started with:

    C-k Instarepl

As soon as you type code into the REPL, it will look for a place to evaluate your code.  If you are already connected to a project then it will allow you to select that.  Otherwise you can either connect to another existing Leiningen project or start a local client.   

When you connect to a project then LightTable is aware of the namespace and you can call the functions and use the definitions within it.

{% img img-code http://2.bp.blogspot.com/-_ZzAf7Q2HX0/UL5Kfkh3nZI/AAAAAAAAIpY/-r6CKiHl4d4/s1600/lighttable-instarepl-connecting.png %}

I my opinion, the **Live evaluation** is the most interesting feature of Instarepl.  This not only gives you the results of you functions but also shows evaluations of the aspects of functions all the way through the code.

I used the Instarepl recently as a great way to introduce 100 Java developers to Clojure and it was really useful to see what was happening underneath.

{% img img-code http://4.bp.blogspot.com/-mEvULZ0TaPc/UL4n855xogI/AAAAAAAAIo4/7ffBhvUgh3g/s1600/lighttable-instarepl-examples.png %}

# Customising LightTable

There are some basic customisations available for LightTable using the `set` command, but they are not persistent (not yet anyway).  Essentially you can change the theme and switch on/off line numbers using the command

Theme and line number changes do not take immediate effect, you need to open a new tab before you see the change. The Welcome screen is never effected by theme changes.

You can resize the font at any time and it even resizes the command line font.  I found a good size for presentation is 14 or 16. 

    set line-numbers true
    set line-numbers false
    set font-size 12
    set theme solarized light
    set theme solarized dark
    set theme default
    set skin light
    set skin dark

All the [codemirror](http://codemirror.net/demo/theme.html) themes are also included, although on my Mac with OSX10.7 they didn't all display exactly the same in LightTable as they did on the demo page.

# LightTable Resources

* [Project home and downloads](http://www.lighttable.com/)
* [LightTable announcements](https://groups.google.com/forum/?fromgroups=#%21forum/light-table) 
* [LightTable discussion group](https://groups.google.com/forum/?fromgroups#%21forum/light-table-discussion)      
* [Github project issues](https://github.com/Kodowa/Light-Table-Playground/issues)        
* [Live game editor](http://github.com/ibdknox/live-cljs) 

Thank you.
[@jr0cket](https://twitter.com/jr0cket)

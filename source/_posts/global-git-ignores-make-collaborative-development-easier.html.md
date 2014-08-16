title: Global Git Ignores make collaborative development easier
date: 2013-02-08 15:22:00
categories: dev-tools
tags: 
- git
---

{% img img-thumbnail http://git-scm.com/images/logo.png %}

Lots of developers are using git, especially when working on projects together.&nbsp; However there is not one single developer tool that every one uses, so there is potential for a lot of unwanted files to end up in your project.

Rather than pollute the .gitignore file for the project with every development tool under the sun, its much more effective to add development tool specific files to your own global ignore file `~/.gitignore_global`.

<!-- more -->

# Creating my own global ignores 

In the `~/.gitconfig` of my home directory I have a section called `[core]` where a global excludes file is defined

    [core]
      excludesfile = /Users/jstevenson/.gitignore_global</span>

By adding file name patters to the `.gitignore_global` file for Emacs, I can add my own personal excludes without adding unnecessary stuff to each project I work on.  It also means its one  less thing to remember when I am working with git projects.

In the root of your home directory, simple create or update the file `.gitignore_global` with all the file names and patterns that relate to the tools you use.

# Ignore patterns 

To help you out, here are some ignore patterns for some of the most common developer tools.&nbsp; There are lots of ignore patterns on the [Git Ignore github repository](https://github.com/github/gitignore/tree/master/Global)

## Emacs ignore patterns

{% img img-thumbnail http://1.bp.blogspot.com/-PLeobToC6lc/TzFJCfBSLPI/AAAAAAAAEbE/zSx1cOgHzZE/s1600/emacs128x128icon.png %}

I use Emacs for much of my development projects, so here are some ignore patters I add to my `.gitignore_global` file

``` .gitignore_golbal
*~
\#*
\#
/.emacs.desktop
/.emacs.desktop.lock
.elc
auto-save-list
tramp
.\#*
```

## Org-mode

I also create a lot of developer content using Emacs Org-mode, so here are the ignore patterns I add for this.

``` .gitignore_global 
.org-id-locations
*_archive
```

## Vi / Vim
.*.s[a-w][a-z]

## IntelliJ ignore patterns

``` .gitignore_global
*.iml
*.ipr
*.iws
.idea/
```

## Netbeans ignore patters

{% img img-thumbnail http://2.bp.blogspot.com/-EjfbbP6MpJo/URUV9U3X4ZI/AAAAAAAAJCY/RagOD9XWMZs/s1600/netbeans-logo.jpg %} 

``` .gitignore_global
nbproject/private/
build/
nbbuild/
dist/
nbdist/
nbactions.xml
nb-configuration.xml


## Eclipse ignore patters

{% img img-thumbnail http://1.bp.blogspot.com/-RmrjIrvG7dE/URUVuk2P5QI/AAAAAAAAJCQ/RGcprIpBxjc/s1600/Eclipse_Icon_by_flosweb.png %}

``` .gitignore_global
*.pydevproject 
.project 
.metadata 
bin/** 
tmp/** 
tmp/**/* 
*.tmp 
*.bak 
*.swp 
*~.nib 
local.properties 
.classpath 
.settings/ 
.loadpath 
.externalToolBuilders/ 
*.launch 
.cproject
.buildp 
```

Thank you.
[@jr0cket](https://twitter.com/jr0cket)


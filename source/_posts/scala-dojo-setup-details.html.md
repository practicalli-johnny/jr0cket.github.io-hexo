title: Scala dojo setup details - LSug coding dojo
date: 2010-05-27 18:45:00
categories: events 
tags: 
- scala
---

{% img img-thumbnail http://upload.wikimedia.org/wikipedia/en/8/85/Scala_logo.png %}

The London Scala user group are holding monthly dojo events to help everyone get to grips with this exciting new language implementation for the Java Virtual Machine (JVM).  A coding dojo is a practial event where everyone decides on a challenge or technology to try out, then getting into groups to code up an application.  The coding dojo concludes with each team doing a show-n-tell of what app they have created and any lessons learnt.

Here are some details of how we set up the tools to help with the London Scala user group coding dojo.

<!-- more -->

# Coding Dojo tools

The following tools were decided upon at a Scala install fest as a collective workshop:

*   Scala Version: [**2.8**](http://www.scala-lang.org/downloads)
*   IDE: [IntelliJ IDEA 9](http://www.jetbrains.com/idea/download/)
*   Build Tool: IntelliJ was used initially, but quickly moved to Simple Build Tool (SBT)
*   Version Control: [**Git**](http://git-scm.com/download)  (also available in Ubuntu repository)
*   Project Resource Hosting: [**Assembla**](http://draft.blogger.com/spaces/lsug-dojo/) 
*   Operating System: [Ubuntu](http://www.ubuntu.com/) (for the dojo laptop - project itself is OS neutral)

A user guide to setting up the tools for the Ubuntu platform are under development and available on the [Assembla LSUG-dojo site](http://www.assembla.com/wiki/show/lsug-dojo/Tools).

# Project hosting

{% img img-topic http://1.bp.blogspot.com/_yKz3swsAoNQ/S_zui-8PnOI/AAAAAAAAAEY/kx9xO4g2eW4/s1600/Scala-Dojo-Assembla-plans-freepublicworkspace.png %}

The dojo code repository, wiki and discussion forum are hosted using the [Assembla](http://www.assembla.com/) project cloud service.

To get a free service, a public workspace was created from the available [Assembla plans](http://www.assembla.com/plans).

For the public workspace I selected the "Git repository with tickets" option to create a new collaborative space

{% img img-thumbnail http://1.bp.blogspot.com/_yKz3swsAoNQ/S_zvk-uv7VI/AAAAAAAAAEg/LfJbcBaRZSs/s1600/Scala-Dojo-Assembla-features-management.png %}

Management tools allow control of the contribution access people have. When you add the project to your assembla account you become a watcher of that workspace.  The workspace owner can then make you a member, giving you contribution level access so you can edit wiki pages and submit code.

{% img img-thumbnail http://4.bp.blogspot.com/_yKz3swsAoNQ/S_zvoyJyT_I/AAAAAAAAAEo/mzSK8xeswEk/s1600/Scala-Dojo-Assembla-features-collaboration.png %}

Collaboration tools are provided by Assembla and include a wiki and a discussions board

{% img img-thumbnail http://3.bp.blogspot.com/_yKz3swsAoNQ/S_04BCiD6DI/AAAAAAAAAFA/13O3PdTr448/s1600/Scala-Dojo-Assembla-features-repository.png %} 

The code repository is git, as that was the chosen option when creating the workspace (subversion is the alternative).  All code can be checked out using a git client using `git://git.assembla.com/lsug-dojo.git`

{% img img-thumbnail http://3.bp.blogspot.com/_yKz3swsAoNQ/S_04Nx6sqEI/AAAAAAAAAFI/_W4hm2lWrKk/s1600/Scala-Dojo-Assembla-features-ticketing.png %}

KTicket management - issue tracking, bug requests, features, stories, etc...

Thank you.
[@jr0cket](https://twitter.com/jr0cket)

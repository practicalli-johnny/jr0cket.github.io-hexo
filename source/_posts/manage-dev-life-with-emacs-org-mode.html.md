title: Manage your developer life with Emacs Org-mode - an overview
date: 2013-08-22 13:39:00
categories: emacs
tags: 
- emacs
- dev-tools
- org-mode
---

{% img img-thumbnail http://1.bp.blogspot.com/-PLeobToC6lc/TzFJCfBSLPI/AAAAAAAAEbE/zSx1cOgHzZE/s1600/emacs128x128icon.png %} 

As a busy developer I end up working on several projects, documents & books at the same time. &nbsp;I want a simple way to capture notes where I don't have to worry about formatting. &nbsp;I also want to keep a track on all the things I am working on. &nbsp;As I do most of my coding &amp; writing with Emacs, then I was sure it had something that could help.

<!-- more -->

## Enter Org-mode
Org-mode is a really simple and beautiful way to take notes, create presentations, organise thoughts and help you manage tasks across all your work. &nbsp;The latest versions of Emacs (23.x / 24.x) have Org-mode built in, so you can use it straight away with `M-x org-mode`.

Org-mode documents are plain text, so they are easy to write and understand even outside of Emacs. &nbsp;The magic is happens when Org-mode interacts with that text. &nbsp;Org-mode understands the structure of the text and lets you easily organise everything into something useful.

I have written [**a simple guide to configuring Org-mode and Org-capture**](http://jr0cket.co.uk/2013/08/configure-emacs-org-mode-to-manage-your-tasks.html.html), as well as** [a guide to creating your own task workflow](http://jr0cket.co.uk/2013/08/defining-custom-workflow-with-Emacs-org-mode.html)** for Org-mode.

Here is a quick YouTube video overview of Org-mode for Emacs by [Richard Dillon](http://www.youtube.com/user/rpdillon?feature=watch), to understand the keyboard short-cuts used (key bindings) then see his [Org-mode notes](https://github.com/rpdillon/hack-emacs-notes) on Github. &nbsp;Or if you are already hooked on the idea of Org-mode then see the In-depth guide at the end of this article.

{% youtube 6W82EdwQhxU %} 
_Hack Emacs: Introduction to Org-mode_

You can also take a look at&nbsp;[Carsten Dominik&nbsp;talking about Org-mode](http://www.youtube.com/watch?v=oJTwQvgfgMM) from the Google Tech Talks back in 2008, the content is still relevant.

{% youtube oJTwQvgfgMM %}


## Using Org-capture to track tasks
Org-capture provides an easy way to create a list of all those tasks you want to do across all the text files you are working with. &nbsp;You create a comment in the file you are working in then with the cursor over that comment you create a new task using **org-capture**.  This opens up a file that holds your current tasks and using a template it creates a task that links back to the file where you made your comment. &nbsp;When you open this link it takes you back to the file and to the exact position you created the task from.

I will show you how to set up and use org-capture with Emacs and Emacs live in the next article of this series.

## Creating presentations for developers
You can easily create an interactive presentation with org-mode and more importantly for developers interact with real source code in a tool that knows how to process that code. &nbsp;If you want to publish this you can put your `.org` file on Github or export your presentation as HTML and other formats.

so you dont need to spend time on creating fancy spinning presentations with JavaScript or yet another boring power point presentation and fill it with static screen shots.

## Learning Org-mode
The best place to start learning Org-mode is its website:&nbsp;[http://orgmode.org/](http://orgmode.org/). &nbsp;I found the [compact guide](http://orgmode.org/guide/) a great introduction and it got me going quickly. &nbsp;I will also be writing a few follow-on articles on specific topics like task management and presentations.

You can also watch the [Emacs Org-mode In-depth video](http://www.youtube.com/watch?v=nsGYet02bEk), again by&nbsp;[Richard Dillon](http://www.youtube.com/user/rpdillon?feature=watch)

{% youtube nsGYet02bEk %}
_Emacs Org-mode in depth_

Thank you.

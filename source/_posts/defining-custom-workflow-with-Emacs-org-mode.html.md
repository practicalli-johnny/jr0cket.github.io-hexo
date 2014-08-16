title: Defining custom task workflows with Emacs Org-mode
date: 2013-08-27 12:00:00
categories: dev-tools
tags: 
- emacs
- orgmode
---

{% img img-thumbnail http://1.bp.blogspot.com/-PLeobToC6lc/TzFJCfBSLPI/AAAAAAAAEbE/zSx1cOgHzZE/s1600/emacs128x128icon.png %}

Org-mode is a great way to track tasks and manage all those to-do items in one place, although Org-mode has a very simple workflow by default **(TODO | DONE)**.  To track your tasks in more detail you can define extra stages or create a completely workflow.

<!-- more -->

Previously I covered [how to set up Org-mode &amp; Org-capture](http://jr0cket.co.uk/2013/08/config-emacs-org-mode-to-manage-tasks.html) for the built in workflow.  In this article I show how to configure Org-mode to use my own custom workflow or define your own multiple workflows should the need arise.

# My Kanban workflow

I like to [organise my work using Kanban](http://jr0cket.co.uk/2011/09/two-years-on-kanban.html), an agile technique that focuses on getting work done by managing workload and learning through fast feedback.  To implement this Kanban approach I define 4 stages for my task workflow:

{% img img-code http://2.bp.blogspot.com/-oLZ24RvCtxw/UhugLxfVpyI/AAAAAAAAK50/p-M0BRiZR6Q/s1600/emacs-org-mode-kanban-coloured-stages.png %} 

# Emacs Org-mode for managing TODO's using a Kanban style workflow

**TODO** - tasks I have not started yet.  If I have an idea for a task, I can make a quick note and get back to what I was doing without loosing focus or worrying about forgetting to do something.

**DOING** - tasks I have started working on.  I try to keep the number of tasks I am doing as low as possible so I am not task switching.  This helps me get things done

**BLOCKED** - tasks that I started working on but cant continue with for some unexpected reason.  I wont start working on these until I have more time set aside to unblock them.  If I block a task with sub-tasks then I will not work on any of those sub-tasks either (I have not seen anything in org-mode to automatically block and unblock sub-tasks if its parent is blocked or unblocked, that would be useful).

**REVIEW** - tasks I have completed but want to check if there something I can learn or share from the experience of doing that task.  This can help me define other tasks related to the one I just completed.

**DONE** - tasks that are completed.  I keep the done tasks around for the week so I have a feeling of accomplishment and avoid repeating myself.

**ARCHIVE** - an optional stage to put tasks in if I want a longer term record of completing that task

# Defining additional task stages 

You can create a new workflow for your tasks by defining setting a sequence of text strings to the variable `org-todo-keywords`

I am using Emacs Live as a base configuration, so I put all my Org-mode configurations into a file called:

    ~/.live-packs/jr0cket-pack/config/org-mode.el

If you are not using Emacs Live you can place them in `~/.emacs.d/init.el`.

Here is an example that implements my Kanban workflow:

    (setq org-todo-keywords 
      '((sequence "TODO" "DOING" "BLOCKED" "REVIEW" "|" "DONE" "ARCHIVED")))

The  vertical bar `|` defines the possible end states for your task.  Org-mode can be configured to add content to your task upon entering an end state, such as setting a `CLOSED` variable to the current date and time stamp.  This is useful if you want track your time spent on tasks.  I will cover this in a follow on article, or see the section on [Progress Logging](http://orgmode.org/org.html#Progress-logging) of the Orgmode tutorial.

# Defining multiple workflows

You can also define multiple workflows so long as all the task stage names are unique.  Here is an [example of multiple workflows](http://orgmode.org/org.html#Workflow-states) from the org-mode.org website:

    (setq org-todo-keywords  '((sequence "TODO" "|" "DONE")
      (sequence "REPORT" "BUG" "KNOWNCAUSE" "|" "FIXED")
      (sequence "|" "CANCELED")))

I haven't found a use for this approach as yet, but will add it to my `TODO` list to investigate.

# Making workflow stages more distinct with colour

The default colours for Org-mode tasks are pink for TODO and Green for DONE.  As we are creating additional steps it helps me scan my task states if they are colour coded.

Here is an example of defining colours for each of the states of my Kanban workflow.  Most of the colours are defined using the text of the name.  The org-warning is used to set the TODO stage to the standard org-mode colour for TODO.

```
;; Setting Colours (faces) for todo states to give clearer view of work 
(setq org-todo-keyword-faces
  '(("TODO" . org-warning)
   ("DOING" . "yellow")
   ("BLOCKED" . "red")
   ("REVIEW" . "orange")
   ("DONE" . "green")
   ("ARCHIVED" .  "blue"))) **</span>
```

# More Org-mode customisation to consider

There are lots more customisations that can be made to Org-mode to help you manage tasks.  Here are some aspects I am considering next.

## Creating more templates for Org-capture

By default Org-capture only has one template, the task template.  This task template only a time stamp of when it was created and a link to the file.  All the TODO items created with this template go under the main heading of Tasks, so I could create templates for other headings such as Personal, Financial, Household, etc.

## Triggering actions on Org-mode stages

When I mark my tasks as done, I'd like to have that tasked automatically date stamped so I know when I completed it.  This would add a `CLOSED` parameter to the task in question.  If I also have time stamps for each of the states then I can track my cycle time and check to see if I am keeping too many tasks in the DOING state.

A lot more features of Org-mode can be found at the excellent [Orgmode.org](http://orgmode.org/) website.

Thank you.
[@jr0cket](https://twitter.com/jr0cket)

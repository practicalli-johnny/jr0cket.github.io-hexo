title: Configuring Emacs Org-mode to managing your tasks
date: 2013-08-26 21:44:00
categories: dev-tools
tags: 
- emacs
- orgmode
---

{% img img-thumbnail http://1.bp.blogspot.com/-PLeobToC6lc/TzFJCfBSLPI/AAAAAAAAEbE/zSx1cOgHzZE/s1600/emacs128x128icon.png %} 

[Emacs Org-mode](http://blog.jr0cket.co.uk/2013/08/manage-dev-life-with-emacs-org-mode.html) has a feature called Org-capture that makes it easy to keep track of all the to-do's that crop up as we work on projects.  With Org-capture you can make comments across all your files and projects and link to them all from one place. 

Here is how to configure Emacs Org-capture so you can quickly create new tasks relevant to specific files and easily manage them all in one place.  If you are not familiar with Emacs Org-mode, take a look at my article: [Manage your developer life with Org-mode](http://blog.jr0cket.co.uk/2013/08/manage-dev-life-with-emacs-org-mode.html).

<!-- more -->

> I use [Emacs Live](http://overtone.github.io/emacs-live/) as a base configuration for Emacs, although everything here will work with any setup as Org-mode and Org-capture are both part of Emacs itself.  If you are not using Emacs live, you can place the configurations in your `~/.emacs.d/init.el` file rather that the locations specified here.

# Using Org-capture todo file to track tasks

Org-capture creates a list of all those tasks you want to do across all the text files you are working with in a single file, by default this file is called `.notes` and lives in the root folder of your account.  However, the file managing your tasks should really have a `.org` extension so that Emacs automatically puts it into org-mode when its loaded. 

You should also consider creating your todo list file where it is easy to manage with Git or a synchronisation service like Dropbox.

{% img img-code http://2.bp.blogspot.com/-1pQtvXL1elc/Uhu9VLK7gXI/AAAAAAAAK6E/4KbFDRdE3oE/s1600/emacs-org-mode-tasks-example.png %}

# Managing tasks using Org-mode and Org-capture

## Define where your tasks are kept

Define a variable called `org-gefault-notes-file` to set the path and file name for the todo file.

I put this variable definition in a new file I created to hold all my Org-mode configurations:

    ~/.live-packs/jr0cket-pack/config/org-mode.el

Then I edited this file and add the following definition for the todo file:

    ;; Define the location of the file to hold tasks
    (setq org-default-notes-file "~/.todo-list.org")

## Calling the custom org-mode settings the Emacs Live way

As I am using Emacs Live, I follow the convention of placing sets of configurations into their own file and calling that from my live-pack init.el.  Editing my `init.el` file I added:

    ~/.live-packs/jr0cket-pack/init.el

and added a new line to load in the configuration from the `org-mode.el` file:

    (live-load-config-file "org-mode.el")

## Adding key bindings for org-capture

I set up a keyboard binding for org-capture using `C-c c` (control key and c, followed by c).  I opened an existing binding file I have in my live pack

    ~/.live-packs/jr0cket-pack/config/bindings.el

and added a definition to call org-capture

    (define-key global-map "C-c c" 'org-capture)

## Create a notes.org file

Create the file that will hold all your tasks by either opening and saving a file of that name in Emacs or using the command:

    touch ~/.todo-list.org

Emacs is now setup to capture all your todos via Org-capture, so lets look at how we use Org-capture

# Creating a task using Org-capture

Open up a source code file or other text file you want to work on.  Create a comment in that file about a TODO / task you want to do.  With the cursor still on your comment, use the org-capture command or the keyboard combo:

    M-x org-capture
    C-c c

You are prompted to choose a template for the type of entry you want to create.  By default there is only one called task.  Press the letter `t` to select the task template.

The cursor will now be in the Org-mode task file you created earlier allowing you to type in a descriptoin of the task.  Updated the task list with this new task using the keyboard combo

    C-c C-c

You can save the tasks file as usual with `C-x C-s`.

## Following links

To open the file that your task links too, or open a web addresses you have added to the task, place the cursor anyware on the link and use

    C-c C-o

# Adding TODO's manually

As has been mentioned previously, org-mode manages tasks using a plain text file, so its easy to add your own tasks by manually editing the file.  You can indicate a task using the * notation.

```
* Level 1 heading
** Level 2 heading
*** Level 3 heading and so ....
```

By default the org-capture function has only one template, Tasks.  So all todo's created with org-capture will be level 2 headings under * Tasks...

** description of task

# **Navigating and using your org-mode task list**

When `~/.todo-list.org` file is in org mode, you may only see the text `Tasks...`.  The three dots after Tasks indicates that this is a heading that contains more underneath.  Using the `Tab` key you can expand the contents and repeatedly tabbing will cycle through different levels of expansion.  To work on all headings at once, you can use the **Shift-Tab** key combination.

**M - Enter**
- creates another line in the same style as the current one the cursor is on.  If you do Alt-Enter at the end of a Task line, a new task is created.  At the end of a list line, a new list item is created, etc.

**Shift- left/right arrows**
- on a TODO text cycles through the states of the task workflow

**M - left/right arrows**
- promotes or demotes the task, giving an quick way to create sub-tasks.  A task line must start at the beginning of the line.  If you indenting a task line with spaces means it is no longer recognised as a task.

**M-Shift- left/right arrows**
- promotes / demotes a whole structure.  For example, if there is a level 2 heading with several level 3 headings underneath, then promoting the level 2 heading to level 1 also promotes the level 3 headings to level 2.

**M-Shift- up/down arrows**
- move tasks and list items up or down within the same level

**Shift - up/down arrows**
- when on task ** will cycle through the priority of a tasks [A, B, C, none]

# In Summary

Emacs Org-mode is a great way to organise your busy developer life - and life in general if you are that way inclined.  As Org-mode is a part of Emacs already, then all you need to do is add a couple of lines of configuration and you are off.

As any Org-mode file is just a text file underneath, then you are not trapped into a format you cannt use anywhere else.

Hope you have a great time organising yourself with Org-mode.

Thank you.
[@jr0cket](https://twitter.com/jr0cket)

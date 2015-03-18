title: Clean Git commits with Emacs Magit
date: 2015-02-09 10:28:30
categories: dev-tools
tags:
- emacs
- git
- magit
---

{% img img-thumbnail /images/emacs-logo.png %}

  An effective way to have a clean and valuable commit history is to create the smallest valuable commit each time, with a descriptive commit message.  This sounds obvious, but when you are in the midst of work things can get messy.  Using Emacs Magit you can be highly selective as to what changes you include in each commit, down to individual characters.

> This follows on from [staging patches for cleaner commits](/2014/07/staging-patches-with-git-for-cleaner-commits.html) with the command line, `git add -p`.  Also see how to [drive Git with Emacs and Magit](/2012/12/driving-git-with-emacs-pure-magic-with.html.html) for more background.

<!-- more -->

## Emacs Magit

  Magit is an amazing tool for managing Git repositories, providing all the standard features of a graphical tool.  It is part of the [Emacs Live](https://github.com/overtone/emacs-live) and available via the useual Emacs package managers.

  To run magit, I typically open a file under version control and hit `C-x g` or `M-x magit-status`.

  Magit keeps track of the changes in your project and the status can be updated using `g` in the magit buffer.

  To stage all the changes in a file you can move the cursor to the unstaged file you want to add and press `s`, or stage all changes using `S`.

  To unstage a file, again move the cursor against its name and press `u` or unstage all files added using `U`.

![Emacs Magit - status buffer](/images/emacs-magit-status.png)


## Selective commits using hunks

  Its easy to be more selective than just staging everything in a file.  Move the cursor against the filename and press `tab` to show the _hunks_ within a file.

> A _hunk_ is the name Git gives to continuous lines that contain changes in a file.  So if all your changes are made line after line, there will be one _hunk_.  If you have unchanged lines between the lines you have changed, you will have more than one _hunk_.

  Move the cusor to the hunk you want to add and pres `s` to stage that hunk.  Using `n` & `p` to move to the next or previous hunks if they exist.

  Sometimes Git organised the changed lines into hunks that have too many changes in, or to few changes.  You can change hunk sizes using  `+` or `-` to expand or shrink the hunk (shrinking is essentially splitting a hunk where possible).

> It may not always be possible to split a hunk enough for your commit.

## Selective commits using regions

  If you really need to refine what you are committing, you can select a region to stage by selecting characters and lines.

  Open a file that has unstaged changes using `tab`

  Select a region of the text using `C-SPC` or `C-@`

  Hit `s` to stage the selected region

![Emacs Magit - select region to stage](/images/emacs-magit-staging-hunk-select-region-to-stage.png)

> Make sure you have not shrunk any hunks, or the region selection may not work.

  You can check the correct text has been added by viewing the newly added entry in _Staged changes_ section.

![](/images/emacs-magit-staging-hunk-select-region-staged.png)

## Summary

  So Emacs Magit give a really easy way to stage changes in the size of commit that is most valuable.  So take a few seconds longer to think about what you are committing and how useful it will be to others and yourself during the life of the project.

  You dont want to be spending too much time unpicking commits to find a bug and applying a patch.

Thank you.
[@jr0cket](https://twitter.com/jr0cket)

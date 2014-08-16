title: Git log makes multiple repos easier to track
date: 2013-01-29 00:42:00
categories: dev-tools
tags: 
- git
---

{% img img-thumbnail http://git-scm.com/images/logo.png %} 

Git is a great developer tool for managing and sharing code.  Its really easy to get started with, especially with services such as [Github](https://github.com/) and their excellent [try.github.com](http://try.github.com/) website.  I quickly became comfortable with the basic developer cycle: 

    git init
    git status 
    git add filename
    git commit -m "useful message"
    git push
    ;; back to git status...
    
To keep track of changes when you just have a local repository is easy with `git status`.

<!-- more -->

# Git log for tracking multiple repositories 

When you start sharing a remote repository then changes are distributed and developers start using `git log` to track changes across repositories.  The challenge with `git log` is that by default you have to scroll through a lot of text to see what is happening.  This gets a bit tedious really quickly.

{% img img-code http://2.bp.blogspot.com/--Oj7Ocw5ddA/UQavWR8_1oI/AAAAAAAAI-M/g1hbsrRRbJ4/s1600/git-log-default-output.png %}

Luckily, the `git log` output is very configurable so its really easy to get a clearer picture.  The most useful options to git log include 

`--abbrev-commit` - only shows the last part of the very long commit name, the sha.  This is now a default option since Git 1.7.x

`--graph` - show an ascii art graph of the commit history, also known as the commit graph.

`--pretty=oneline` or `--oneline` - print each commit entry on a sigle line, which can be scrolled horizontally to see longer commit messages.  The one-line value is one of several built in formats to the --pretty option and in this case can be used as an option on its own.

`--decorate` - shows the forks, branches and tag names relative to the commit history, helping you keep track of latest commit on each branch and across all your remote repositories.  Decorate therefore provides a quick way to see which commits have been merged or pushed.

Putting all these options together you get a much simpler and easier to follow view of the commit history.

{% img img-code http://2.bp.blogspot.com/-s_hKo72A__c/UQcUcUJP71I/AAAAAAAAI_M/Zf0G9Zi_1b0/s1600/git-log-commit-graph-decorate-oneline-abbrev-commit.png %} 

# Creating git aliases

Rather than type git log and all these options each time (or scroll through your shell history), you can create a git alias as a shortcut for this long command line

I create an alias called `lg` for git log as follows:

    git config --global alias.lg 'log --graph --oneline --decorate'

This will add the alias called lg to your `~/.gitconfig` file.  You could also edit this file directly and add aliases manually.

    <pre>`[alias]
        lg = log --graph --oneline --decorate

# The commit graph

Visualising the commit graph is my must-have tool when using git, I use it nearly as often as `git status`.  The commit graph shows a history of commits and the position of repos in that history.  When there are branches, this is rendered as a tree-like structure and it is easy to see the relative status of your local and remote repositories attached to the project.

{% img img-code http://1.bp.blogspot.com/-iDu7u9zb1oA/UQcU1yeQWyI/AAAAAAAAI_U/ML7tNMPDmRc/s1600/git-commit-graph-stylised.png %}

Most common status in git is to have your local repository ahead of the remote masters in terms of commits, with **HEAD** pointing to you local repo. Its quite common to do a group of related commits locally before pushing then to a shared remote repo.  When the remote repo is behind your local repo, this is quite obvious from the commit graph, as its on an earlier commit version and therefore a different line of the graph.

You can see when a push happens to a remote repository from your local repo, as the branch merges into the trunk.  When everything that has been committed locally has been pushed then you can see the remote branch at the same commit version as the local.

In the situation where you have multiple repositories, for different stages of the development workflow (for example testing, staging, CI), the commit graph really makes the status of your different repositories really clear.  You can see at a glance the commit version each repo is on.  The commit graph also helps you understand which commits to push to which repos.  This is also invaluable when merging two longer running branches (should you get to that situation).

# Designing your own commit graph 

In the next article I will cover how to create your own design for the git commit graph, creating several aliases for different levels of information 

Thank you.
[jr0cket](https://twitter.com/jr0cket)

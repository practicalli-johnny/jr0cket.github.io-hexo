title: Designing your own commit graph with git
date: 2013-06-22 19:40:00
categories: dev-tools
tags: 
- git
---

{% img img-thumbnail http://git-scm.com/images/logo.png %}

Git log is a very powerful tool for tracking all your changes, even across different branches and multiple repositories.  However <span style="font-family: Courier New, Courier, monospace;">git log</span> default output is verbose and not a great way to visualise the commit history.

Fortunately Git is very customisable, both for humans and tools.  This article covers one way to creating your own customised output for git log that helps you work with branches and track changes through local and remote (eg. Github) repositories.

<!-- more -->

# Using git log options

In a [previous article](http://blog.jr0cket.co.uk/2013/01/git-log-makes-multiple-repos-easier-to.html) I covered the different git log options that could be combined into a good visualisation:

    git log --graph --decorate --relative-date --oneline
    
This is a very simple way to configure the log, but there is a lot more you can do to tweak this.

# Hacking the pretty format

For any git output you can use the `--pretty=format:` option to define your own visualisation of the information.  There are some built in formats you can use with this option or with a bit of googling its not to hard to create your own specific layouts and colours.

Lets look at an example git log configuration:


    git log --graph --date=relative 
            --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr)%Creset'

Show the git log graph with date relative times to the last commit made.  Commit numbers are in red, branches and remote repositories are in yellow, commits in white and relative commit times in green.

{% img img-code http://4.bp.blogspot.com/-8qgVMXGUang/UcXd207WTwI/AAAAAAAAJyg/FXf3u6vSi4c/s1600/git-log-pretty-one.png %}

Lets add commit author details to the configuration too:

    git log --graph --date=relative 
            --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)&lt;%an&gt;%Creset'

The author information is added to the end of each line in blue.

{% img img-code http://2.bp.blogspot.com/-k3GFOHCIE3Y/UcXeFBv-ZaI/AAAAAAAAJyo/PV1fyHbgbzU/s1600/git-log-pretty-two.png %}

            
This example shows you the full history of your git log 

    git log --graph --full-history --all --color --date=short 
            --pretty=format:'%Cred%x09%h %Creset%ad%Cblue%d %Creset %s %C(bold)(%an)%Creset'

A simpler git log in graph form 

    git log --graph 
            --pretty=format:'%Cred%h%Creset - %C(yellow)%d%Creset %s %Cgreen%cr %C(cyan)[%aN]%Creset'

You can also create a simple commit graph by date, without showing the numbers.  This is useful if you are just going off the branches or tags. 

    git log --graph --date=short
            --pretty=format:'%Cgreen%cd%Creset - %C(yellow)%d%Creset %s %C(cyan)[%aN]%Creset' 


# Adding Shortcuts for git log options 

You can add these commands and many more to your git config file as aliases to save your typing them all out and having to remember them too.  You can use git config or add them directly to your `~/.gitconfig` file as follows:

{% gist 4649149 %}

# Understanding the Git Pretty Format codes

There is a complete [guide to git](http://opensource.apple.com/source/Git/Git-19/src/git-htmldocs/pretty-formats.txt) formats and codes, however these are probably the main codes you need to know

* output text in the colour colour-name
    %Ccolour-name 

* reset the output text colour
    %Creset

* commit number / hash (in short form due to the `--abbrev-commit `option) 
    %h

* repository (--decorate) 
    %d

* commit message 
    %s

* time stamp / commit relative 
    %cr

* author / account name
    %an

# Abbreviating Commit numbers

Since git version 1.7.6, git config has gained a `log.abbrevCommit` option which always abreviate commit numbers in any git output.  

    git config --global log.abbrevCommit true

If you are using the `--oneline` option on git log, then the commit number is abreviated regardless of this setting.

# In Summary

Have fun configuring your git log as if you use git on the command line you will be working with the log quite often.  However, dont spend all your time tweaking the format of the log, you still need to write some code for your apps :)

Thank you.
[@jr0cket](https://twitter.com/jr0cket)

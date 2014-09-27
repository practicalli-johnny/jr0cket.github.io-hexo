title: Gith and Github Workshop
date: 2014-08-24 18:22:00
---

This tutorial will give you a practical guide to using the Git tool for version control, so you can easily managing changes to source code and configuration files in projects.  The tutorial also covers collaborating on projects using Github public repositories.  

> Please read [an overview of Git](overview-of-git.html) if you want more background into the tool and how distributed version control works.

## Setting up Git & Github 
- [Choose your git client](choose-your-git-client.html)
- [Identify yourself to Git](identify-yourself-to-git.html)
- [Create an account on Github](create-account-on-github.html)



## Creating Git Projects
* [Creating a Git managed project](creating-a-git-managed-project.html)
* [Ignoring files](ignoring-files.html)


## Local Git Workflow
* Checking the status - what has changed -- git status, git diff 
* Staging changes  - basic add, git add -p, unstaging untracked files, unstaging tracked files, git diff --cached 
* Committing a new version 
* Git log 

* [The local git workflow](local-git-workflow.html)


## Branching & Merging  - why do this
- try out code and modifications to design, different algorithms 
- easily discard changes that are not needed - or leave them in a branch so they are not affecting / poluting the main codebase

* [Branching and Merging](branch-and-merge.html)
* [merging changes](merging-changes.html)



## Collaborating with other developers using Git and Github 
* [Collaborating with Github](collaborating-with-github.html)
* Practices to avoid when using shared repos like Github
- rebasing, forgetting to push changes (especially for sub modules)


## Troubleshooting]
- what to do if you loose your head 
- if you really have to change a commit
- unstage changes


## Resources 
 * Git submodules


# Git in two minutes 

If you have installed Git and know roughly how git works and just want the commands, here is the workflow:

    # Tell Git who you are (only done once)
    git config --global user.name "your name"
    git config --global user.email "your.name@domain.com"

    # Initialise a local repository
    git init
    
    # Tell Git which files you want to make part of the next commit
    git add filename   ; to add a specific file
    git add .          ; to add everything
    
    # Commit those files into a new version 
    git commit -m "meaningful commit message"
    
    # Push your code to a remote repository
    git remote add repo-name git@github.com:github-account/repo-name.git
    git push repo-name master
 
 See my [Git cheet sheet](/developer-guides/git-quickstart-guide.png) for the most common commands for using Git

# Git local workflow visualised 

You can quickly get versioning your code with Git, all on your own computer.  You do not need to set up a server.

<img class="img-code" src="images/git-local-workflow.png">

# Git and Github workflow visualised

To give you a big picture view of how you use Git and Github, here is a visualisation of the workflow for both.  The details of this workflow are ocvered in the workshop from [Chapter 10: Collaborating with Github](chapter10-collaborating-with-github.html) onwards.

<img class="img-code" src="images/git-and-github-workflow.png">

# Reference

* [Git commands cheat sheet](https://na1.salesforce.com/help/doc/en/salesforce_git_developer_cheatsheet.pdf)
* [Git Visual cheat sheet](http://ndpsoftware.com/git-cheatsheet.html)
* [StarLogs.net demo with this workshop](http://starlogs.net/#salesforce-heroku-workshops/git-and-github-workshop)
* [Github repository for this workshop](http://jr0cket.github.io/jr0cket.github.io-hexo/) - pull requests welcome :)

[Back to top...](#top)

Last update: March 19 July, 2014


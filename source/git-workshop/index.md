title: Git and Github Workshop
date: 2014-08-24 18:22:00
---

This tutorial will give you a practical guide to using the Git tool for version control, so you can easily managing changes to source code and configuration files in projects.  The tutorial also covers collaborating on projects using Github public repositories.  

If you just want a very quick start, take a look at [Git in two minutes](git-in-two-minutes.html).

> Please read [an overview of Git](overview-of-git.html) if you want more background into the tool and how distributed version control works.



## Setting up Git & Github 
- [Choose your git client](choose-your-git-client.html)
- [Identify yourself to Git](identify-yourself-to-git.html)
- [Create an account on Github](create-account-on-github.html)



## Creating Git Projects
* [Creating a Git managed project](creating-a-git-managed-project.html)
* [Creating projects with build tools](creating-projects-with-buildtools.html)
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


## Things to look at

Stuff to look at
git reflog -- lists all the commits that you ever did

git bisect -- binary search on your git history 
git bisect good <hash>
git bisect bad <hash>
git bisect reset

git hooks 



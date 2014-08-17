

# <a id="top">Git & Github workshop</a>

This tutorial will give you an introduction to using the Git version control tool, commonly used to managing changes to source code and configuration files in projects.  The tutorial also covers collaborating in teams using Github public repositories.

* [Chapter 1: Git overview](chapter01-git-overview.html)
* [Chapter 2: Choose your git client](chapter02-choose-your-git-client.html)
* [Chapter 3: Create an account on Github](chapter03-create-account-on-github.html)
* [Chapter 4: Identify yourself to Git](chapter04-identify-yourself-to-git.html)
* [Chapter 5: Creating a Git managed project](chapter05-creating-a-git-managed-project.html)
* [Chapter 6: Ignoring files](chapter06-ignoring-files.html)
* [Chapter 7: The local git workflow](chapter07-local-git-workflow.html)
* [Chapter 8: Conflict resolution - managine the merge process](chapter08-conflict-resolution.html)
* [Chapter 9: Branching and Merging](chapter09-branch-and-merge.html)
* [Chapter 10: Collaborating with Github](chapter10-collaborating-with-github.html)
* [Appendix A: Where to go next](#appendix-a)


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
[StarLogs.net demo with this workshop](http://starlogs.net/#salesforce-heroku-workshops/git-and-github-workshop)
* [Github repository for this workshop](http://jr0cket.github.io/jr0cket.github.io-hexo/) - pull requests welcome :)

[Back to top...](#top)

Last update: March 19 July, 2014


title: Gith in Two minutes 
date: 2014-09-27 09:88:00
---

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



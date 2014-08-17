<link href="index.css" rel="stylesheet" type="text/css">

# Managing multiple repositories with Git Logs

  Keep track of changes when you only have a local repository is easy with git status.

  Once you have created your Heroku application you have two repositories to work with, the local repository in your project .git folder and the remote repository at Heroku.
 
  Using git push it is really easy to share all your local changes with the remote repository and other developers working on the application can access them.  

  If you want to see which changes you have pushed to heroku, you can use the Heroku website and you can also use git log.  If you are using the command line to push changes to heroku, then having a good git log setup is important.  By default git log is not that useful and you have to scroll through a lot of text to see what is happening.  This gets a bit tedious really quickly.

  Managing multiple repositories with git log can save you some confusion.

## Setting up a useful git log

  The output of git log output is highly configurable so its really easy to get a clear picture of your commits across multiple repositories.  The most useful options to git log include

**--abbrev-commit**
Only shows the last part of the very long commit name, the sha.

**--graph**
Show an ascii graph of the commit history, also known as the commit graph.

**--pretty=oneline or --oneline**
Print the output onto one line.  The one-line value is one of several built in formats to the --pretty option and in this case can be used as an option on its own.

**--decorate**
Show the branch and tag names relative to the commit history, essential if you want to keep track of which commit version your remote repositories are at.

Putting all these options together you get a much simpler and easier to follow view of the commit history.

<a href="images/"><img src="images/"></a>

## Creating git aliases
  Rather than type git log and all these options each time (or scroll through your shell history), you can create a git alias as a shortcut for this long command line and many others.  Aliases in git are similar to those of the command line shell.

Create an alias called lg for git as follows:

    git config --global alias.lg 'log --graph --oneline --decorate --abbrev-commit'

  This command will add the alias called **lg** to your  ~/.gitconfig file.  You could also edit this file directly and add aliases manually.

    [alias]
        lg = log --graph --oneline --decorate --abbrev-commit


  Git is a great developer tool for managing and sharing code across multiple repositories.  Its really easy to collaborage on projects, especially with services such as Github.  You should quickly become comfortable with the developer workflow around git:

    git init
    git status
    git add filename
    git commit -m "useful message"
    git push
    git log
    ;; back to git status...


# The commit graph

  Visualising the commit graph is my must-have tool when using git, I use it nearly as often as my most used command; git status.  The commit graph shows a history of commits and the position of repos in that history.  When there are branches, this is rendered as a tree-like structure and it is easy to see the relative status of your local and remote repositories attached to the project.

  Most common status in git is to have your local repository ahead of the remote masters in terms of commits, with HEAD pointing to you local repo. Its quite common to do a group of related commits locally before pushing then to a shared remote repo.  When the remote repo is behind your local repo, this is quite obvious from the commit graph, as its on an earlier commit version and therefore a different line of the graph.

  You can see when a push happens to a remote repository from your local repo, as the branch merges into the trunk.  When everything that has been committed locally has been pushed then you can see the remote branch at the same commit version as the local.

  In the situation where you have multiple repositories, for different stages of the development workflow (for example testing, staging, CI), the commit graph really makes the status of your different repositories really clear.  You can see at a glance the commit version each repo is on.  The commit graph also helps you understand which commits to push to which repos.  This is also invaluable when merging two longer running branches (should you get to that situation).


[Back to workshop home](index.html)


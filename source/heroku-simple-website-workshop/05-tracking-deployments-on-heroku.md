# Tracking deployments on Heroku

  You can use information from Git to track which version of your code has been deployed to each of your heroku environments.  As your local repository is linked to the remote repositories that drive your heroku environments, you can see this all the repository information from your local development environment.
  

# Working with Git Log

  Git log shows you the history of the commits you have already made to your local repository.

    git log

  By default, git log has a very basic output and lists that information in a way that is hard to visualise.  You can add options to the git log command to get a much nicer and more useful output, even showing which commits have been pushed to related remote repositories.  

    git log --graph --oneline --decorate --date-relative

  You can add this to your git configuration as an alias so you dont have to type it all the time.

    git config --global alias.lg 'log --graph --oneline --decorate --date-relative'

> Note: you can create an alias with any name that is meaningful to you.  In this example the alisas is called lg*

  Once you have added the alias, you can then use it with the git command:
  
    git lg

> You could also create an alias called gitlog for the command line directly, however, ensure you are not creating a alias names the same as another common command.

## Tracking commits & deploymets

  The customised view of the git log allows us to see which commit version each of our reposiotiries are using.  Using the --decorate option, each remote repository shows up against the commit number it last recieved.
  
> TODO:  screenshots showing how the --decorate option on git log allows you to easily see which commit has been deployed to each Heroku environment.
  
  Using Git and the git log information gives a completely traceable deployment across all your environments.
  
## Blogs on customising git log 
* [Git basic tips and tricks](http://git-scm.com/book/en/Git-Basics-Tips-and-Tricks)
* [Must have alias examples](http://durdn.com/blog/2012/11/22/must-have-git-aliases-advanced-examples/)

  There are many graphical tools for Git.  One of the most feature rich is SourceTree (MacOSX, Windows).   

# Heroku Web console: Activity tab

  There is an activity section on the Heroku website for each application you create on Heroku.  This activity section displays all the releases of your application.
  
  A release is a new instance of your application, running in a new dyno.  A release can be caused by one of the following actions:
  
  * A new commit is sent to the Heroku app using `git push heroku master`
  * An environment variable is set or 
  
  Once a release has completed, the dyno running your previous release will no longer have requests routed to it.

> TODO: screenshots of activity tab, linking github repository to heroku app

> TODO: Using Github with Heroku - benefits / workflow
> TODO: Connecting Github repository to your heroku application


[Back to top...](#top)
[Chapter 06 - Logging on Heroku](06-logs-on-heroku.html)
[Back to Workshop home](index.html)

# <a id="top">Chapter 2: Manage project with Git</a>

  Developers save a huge amount of time when the source code of a project is vesioned.  Understanding what has changes and who has changed it is an important part of the codebase.  Using a distributed version control systems like Git also allows developers to collaborate effectively too.  You can share specific changes you are making across branches and different repositories.  
  
  When using a service like Github you can easily collaborate on projects and have easy code reviews via the use of pull requests.  If you are not famililar with Git, please see the tutorial on Using [Git and Github](http://git-and-github-workshop.herokuapp.com/).

  You should make sure you have your Git **user.name** and **user.email** set, to make it clear who has created each commit.  Again, see the [Git and Github](http://jr0cket.co.uk/git-workshop/) tutorial for help with this. 
  

## Version the project with Git

  A git client was added when you installed the Heroku Toolbelt, but you can also use any you have already installed.  
  
  Now you have created your Meteor project, you will use Git to put your project under version control.  This will create a local git repository which is contained within a folder called *.git*.  It is therefore important that you never delete the .git folder as you will loose your version control history.

  Create (initialise) a new git repository inside your project folder

    cd leaderboard
    git init

  You should now have an empty local git repository in which to manage your changes.  

<img class="img-code" src="images/02x01-create-local-git-repository.png">

  Check this worked by viewing the current status of your git repository

    git status

 You should see a list of files that are not currently tracked by git.

<img class="img-code" src="images/02x02-git-status-of-project.png">

  Add the project files to your git repository & commit the changes:

    git add .
    git commit -m "Initial JavaScript Meteor project created"

> If you do not include the -m option when committing, your default text editor will open so you can enter a commit message.  If not set on MacOSX or Linux, this editor will be vim.  To close vim and write the text, press the Esc key followed by :wq


<img class="img-code" src="images/02x03-git-add-commit.png">

> Make sure the .meteor folder is added to git otherwise Heroku will not recognise your project as a Meteor project   

## Some files dont belong in your projects

  You can tell git to not include certain files, folders and name patterns, so when you do a `git add .` then these files wont be added by mistake.
  
  This is done by creating a `.gitignore` file in your project.  When you create an application using the meteor command line, it creates `.gitignore` file for you, with the default file and folder exclusions for your Meteor project.
  
  If you are using an editor, IDE or operating system that creates its own files and folders that you dont want to include in your project, you should create a global git ignore file in your home directory.
  
    ~/.gitignore_global

  The files and folders you add in the global gitignore file will be excluded from all your projects managed with Git.  The `.gitignore` file will only exclude files and folders from its specific project.

    git config --global core.excludesfile '~/.gitignore_global'

  
  See the [global folder of the Github gitignore repository](https://github.com/github/gitignore/tree/master/Global) for suitable global gitignore files for your development tools (eg. [Eclipse](https://github.com/github/gitignore/blob/master/Global/Eclipse.gitignore), [Emacs](https://github.com/github/gitignore/blob/master/Global/Emacs.gitignore), [InteliJ](https://github.com/github/gitignore/blob/master/Global/IntelliJ.gitignore), [Netbeans](https://github.com/github/gitignore/blob/master/Global/NetBeans.gitignore)).


[Next](03-deploy-your-application-on-heroku.html)
[Back to top...](#top)
[Back to Workshop Home](/index.html)





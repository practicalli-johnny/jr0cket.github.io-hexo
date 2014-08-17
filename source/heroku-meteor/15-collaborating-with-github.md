<link href="index.css" rel="stylesheet" type="text/css">

# <a id="chapter">Chapter : Collaborating on projects</a>

  As you are using git to version control your project, you can also use it to collaborate with other developers and teams.

## Collaborating via Heroku

  Anyone with an Heroku account can be added to your project as a collaborator.  This will allow them to deploy updates (git push) to your application on Heroku directly.  Collaborators can also see the status of your application, change the resources used and enable or remove addons for your app.

  Anyone who is added as a collaborator should therefore understand their responsibilities, especially if they are added to a prodution application.

  To add a collaborator via the Heroku website:

  1. Visit your appliations on the Heroku website
  2. Go to the `Collaboration` tab
  3. Type in the Heroku account name of the person you want to add.


## Collaborating via Github

  Anyone with a Github account can collaborate, regardless of if they have an Heroku account.  This is a much safer way to collaborate and enables use of Github aspects including pull requests.

  Only one person needs to have an Heroku account to push the changes up to the project.  You can make your Heroku app as collaborative as your developers feel is appropriate.

  To collaborate via Github

  1. Create a new repository on Github
  2. Add any collaborators you wish using their Github account name (or send them a link to your repository, so the can fork it and send you pull requests).
  3. Add this new Github repository to your project, run the following within the top level folder of your project (where .git folder lives):

    git remote add git@github.com:account-name/repo-name


  Using `git log` you can to see the state of the repos you have linked to your local repository.  To make this easier to see, you can configure the output of git log to display the commit log.


![command-line-git-log-commit-graph-image][]

  You can also use a git tool such as Source Tree (MacOSX) to show off the commit graph

![source-tree-commit-graph-image]()



[Back to Workshop home](index.html)


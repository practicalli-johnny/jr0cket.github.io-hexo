# A beginners guide to Git and Github

This is a step by step guide to getting going with Git, the distributed version control system.

The workshop is deployed on Heroku at: [http://git-and-github-workshop.herokuapp.com/](http://git-and-github-workshop.herokuapp.com/).

This guide covers the essential features so you can start to use Git to manage your changes in a local repository and then moves on to Github so you can share your managed code with the outside world.

* git command line / graphical tool set up on your laptop
* understanding staging, committing and pushing changes
* working with git status and git log to manage changes
* experience using github for new repos as well as forking & cloning
* managing multiple repositories easily with git log
* working with pull request

This workshop is focused on using git as a developer and will not be diving under the covers of git, or covering any implementation details.


Creating a markdown driven website on Heroku
==========================

To create and deploy a static web site from Markdown files on Heroku, using the following instructions:

1. Create a folder for your project and start writing your content.  You should use an `index.md` file as you website home page:

2. Inside your project folder, create a git repo containing the file:

        cd my-project-folder
        git init
        git add index.md
        git commit -m "Initial project setup"

3. Once the project is under git control, lets create an Heroku application on which to deploy it.  As we are doing something a little different from the usual, we need to specify a specific build pack to tell Heroku how to build, deploy and run our website:

        heroku create --buildpack https://github.com/jamesward/heroku-buildpack-markdown.git

You can optionally specify a name for your website whilst creating it, although this name must be unique within the herokuapps.com domain:

        heroku create --buildpack https://github.com/jamesward/heroku-buildpack-markdown.git my-project-name

4. Now your Heroku app is created, an extra remote repository is added to your local git project.  So now you can push the changes in your local repo to Heroku, deploying the website:

        git push heroku master

5. Once deployed you can open your web site with the following heroku command (or just copy the address given at the end of the Heroku deploy message):

        heroku open

6. Continue to develop your content and committing changes to your local repository.  When you want to publish your changes to heroku, simply do another push:

        git add .
        git commit -m "useful commit message"
        git push heroku master


Also consider creating a repository on Github should you wish to collaborate on the content with others, especially if you have more content contributors than those you wish to be able to deploy to heroku.

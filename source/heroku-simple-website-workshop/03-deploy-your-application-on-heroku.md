# <a id="top">Chapter 3: Deploy your application on Heroku </a>

  You have a working Meteor appliction running locally, it does not do very much but it works.  Now we will discover how to deploy to heroku and have a live application accessible via the Internet.  This gives us a website to test our application and a place for other people to visit to see our work as it evolves.
  
> Although your application is publicly available once its deployed on Heroku, unless someone has the unique web address they wont be able to find it.  Heroku does not provide a public list of deployed applicaitons, so the world wont see it until you tell it your website address.

## Creating your Heroku application

To create a new Heroku application you use the command `heroku create` in the root of your project folder.  This command will create
  
  * A website address for your application 
  * An Heroku Git repository which will recieve your code for deployment

Creating an Heroku application is a little more involved than normal, as we need to specify a buildpack.  Meteor is not one of the supported frameworks as yet, so Heroku will use the information in the buildpack to deploy your application.
  
Create an Heroku application for meteor as follows:
  
    heroku create --buildpack https://github.com/jr0cket/heroku-buildpack-meteor.git

You should get an output similar to the following (although you will have a unqiue name for your heroku app):

    Creating damp-sands-1586... done, stack is cedar
    BUILDPACK_URL=https://github.com/jr0cket/heroku-buildpack-meteor.git
    http://damp-sands-1586.herokuapp.com/ | git@heroku.com:damp-sands-1586.git
    Git remote heroku added

You will notice that a new remote repository called heroku has been added to your git settings, this is the address of the git repository at Heroku you will upload to in order to deploy your code.  
  
If you want to check the heroku remote was added (or if you forget at any time what it was called) you can use the standard git command:
  
    git remote -v

<img class="img-code" src="images/03x02-git-remote-v.png">

When you created your Heroku application, you could have choosen to specify a specific name for your application.  The name used forms part of the website address (name.herokuapp.com), so that name must be unique across all Heroku applications.

    heroku create my-unique-app-name

You can change the name of your application on Heroku later.  If you do, you will also have to update the address of the Heroku remote repository using 'git remote set-url heroku the-new-address'


## Pushing your project to Heroku

  Once you have an Heroku application, you can push any commited project source code to the Heroku git repository which was added when you created the application.  To check that you actually put your code into git, you can use the git log to check what was last commited.
  
    git log

<img class="img-code" src="images/03x03-git-log.png"></a>
  
  Your have code in your local git repository for your project, so you can push that up to Heroku using the standard git push command

    git push heroku master

> Note: As this workshop uses a buildpack that commissinos an addon during the deployment cycle, you need to add a credit card to your heroku account or the git push will fail.

  Everything you committed to your local repository will now be pushed up to the remote Heroku git repository securely (using a secure shell connection).  Git also compresses the commits before sending them to Heroku, so that the minimum bandwidth is used. Once the Heroku repository is updated with the push, this will trigger the building, deploying and running of your application automatically.

  The first time you deploy your project, the environment will be set up on Heroku.  Depending on the size of your application and framework, this could take a little time.  In this workshop as we are using Meteor it should talk less than 30 seconds.
  
  Meteor and all its project dependencies (external libraries) will be downloaded.   
  
> Heroku keeps a mirror of many common libraries, reducing the time it takes to establish the environment and pull in dependencies.  This is really good for speading up the process each time you deploy.
  

## Check your application is running on Heroku

  At any time you can open your application by loging into the heroku website and viewing your apps.  You can also open the specific application you are working on via the command line. 
  
  In your project folder, use the command:

    heroku open

  When you pushed your changes to the Heroku git repository you are also shown the application URL on successful deployment.  You can copy/paste that address into your browser.

  You can now visit the website of your live application and give that address to others.
  

[Back to top...](#top)
[Chapter 04 - Developer workflow for git and Heroku](04-developer-workflow-for-git-and-heroku.html)
[Back to Workshop home](index.html)


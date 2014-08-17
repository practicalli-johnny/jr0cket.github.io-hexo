# Heroku workshop - JavaScript and Meteor workshop - WIP

TODO: CCT DevZone presentation - add slides on how to get going with Heroku - ie. creating a new app, or deploying an existing app.  With existing apps, its an opportunity to refactor the app and can be a way to reduce the risk of dealing with legacy systems (because you can break up your app into several different process and break out functionality across several heroku applications).  This is an extension of where heroku fits into the salesforce world.  Perhaps mention Domain Driven Design.

TODO: create a stle for italics tag that changes the background colour (and perhaps puts a nice box around the text.

TODO:  Create a github repository with the built app, with tags to demark the different steps of development 

Stories of other people converting their apps 

- the tryclj story 
--- took all of 30 minutes to convert the project to heorku.  That consisted of 5 minutes reading how heroku works, 20 minutes realising the project needed a Procfile (to identify the starting point of the application) and a couple of minutes to create the Heroku app, push the code and wait for the dependencies to be pulled in.  Link to blog article.


# Aspects of Heroku to show

## Setting up account
-- need to add your credit card details 

## Installing Toolbelt
-- heroku commands [app: ps: ...]

## Where to get help 

Developer center (Documentation)

stack exchange Heroku tag
meetups




## Creating an Heroku app
-- creating an app
-- Highlighting supported languages & buildpacks
-- creating apps in different regions

## Versioning your app with Git 
-- setting up git (user.name / user.email / public key - heroku keys)
-- creating a local repository
-- adding & commiting files (mention staging & developer workflow)

## Deploying your application on Heroku
-- creating an app
-- adding a remote git repo addreess & alias
-- using git to deploy 
-- basics of continuous deployment


## Tracking your deployments
-- Git log for tracking deployments
-- Activity section on the Heroku website 
-- Configuring git logs
-- Using Git GUI tools (SourceTree, ... [TODO: good gui tool for Linux])
-- Using Github with Heroku - benefits / workflow 
-- Connecting Github repository to your heroku application 


## Heroku and logging
-- introduce logplex
-- Displaying heroku logs 
-- Showing only specific Logs
-- show errors in logs
-- persisting logs (eg. to meet company policies, legal requirements)


## Rollbacks and managing failures
-- discuss heroku releases and rollbacks 
-- create a bug and push it to the heroku app
-- list releases, show release details, rollback to a releases, push a real fix



## Extending the deveployment workflow 
-- the merits and challenges of different environments (testing, staging, UAT)
-- creating multiple environments on Heroku (all the same, always the same)
-- managing deployment across environments with Git log
-- deploying to heroku from branches (other than master)





## Processes and the Procfile
-- introduce the Procfile
-- introduce the web: process type
-- discuss other process types (everything else)
-- working with heroku processes 
-- heroku ps
-- heroku ps:restart


## How Heroku works (high level)
-- buildpacks in more detail - the supported service - choosing your languages & application stack is put together 
-- detecting your app 
-- compiling code 
-- pulling in dependencies 
-- setting up data sources
-- deploying the app 
-- processes - scaling across a "server" 
-- dynos - scaling across multiple "servers"
-- supported languages & frameworks
-- buildpacks for everything else



## Scaling your apps
-- monitoring the performance of your apps
-- new relic addon
-- load testing your app with [apache jmeter | grinder | some online service]


## Enhancing your apps with addons 
-- how to manage addons 
-- common addons used (New Relic, Reddis, Mongodb, ...)


## Mongodb addon with Meteor

-- Using MongoLab addon  web console

View the collections created
View the documents in each collection 
View the data in each documents

 
-- using GUI client for mongodb access


<!-- Review Heroku Postgres service and develop Elevate content around it -->
## Postgres database
-- database on demand
-- forking, following
-- dataclips




## Releases and rollbacks - leave this till later

  What happens when you make a mistake in your code? Let’s try removing one of the double quotes and see what happens:








## Collaborating with Github 

As your using git to deploy your application on heroku, then its makes sense to collaborate on code changes using a service like Github.  Using a shared repository outside of heroku allows you to commit much finer grained changes to a shared repository, an effective way to minimise merge conflicts.

If you created a repository on Github and cloned it locally when you started your project, then its just a matter of adding your team to the repository as collaborators and doing regular pushes of changes.

If you just set up a project with a local git repository, git init, then you can use the git remote add command to add the URL address of a shared repository that you setup.  Assuming you are using github for the shared repository you would do something like:

git remote add github git@github.com:user-name/repo-name.git




Now reload the home page in your browser:

<a href=images/04x01-play-error-hello-world.png"><img src="images/04x01-play-error-hello-world.png"></a>

  Fix the error by adding back in the double quote you removed and save the file.  Check your application is still working by refreshing the browser.





# Meteorite

Meteorite is definitely still relevant and recent talks from meteor team indicate it will be folded into meteor itself eventually.

Meteorite does more than NPM, it also takes client side 3rd party libraries and specifies how they get integrated into a meteor app. In this aspect it serves the same purpose as yeoman/bower. 3rd party client side libraries like x-editable, sugar.js, moment.js, etc dont really belong in NPM, but you also shouldnt have to manually incorporate them into your meteor project either. See this comment from the meteor team: https://github.com/meteor/meteor/pull/516#issuecomment-12919473

Meteorite doesnt provide the full functionality of NPM. With just meteor, you cant just require a NPM package in your app and use it, even in 0.6.0+ you still have to make a package and an api wrapper. If you wanted to use a certain NPM and it was already wrapped and shared on meteorite, that would in effect provide a NPM 'proxy' via a meteorite package. Like this package https://atmosphere.meteor.com/package/ncp

I would suggest using meteorite for the capabilities you gain beyond meteor itself. However, be aware that this is an area in great flux so you may have to rework/adjust your project in the near term. IMO if you are building more than simplistic apps, you'll definitely want meteorite for the ease of incorporating 3rd party libraries.
	

Meteorite is still relevant at this point. Even though NPM packages are supported in meteor there isn't a community repo to add packages from (http://atmosphere.meteor.com)

Even though NPM modules can now be added they still need to be made to work with meteor.

Meteor code uses fibers to allow sync code to run so each NPM module being used still needs a package to let it be used in meteor which can make it easier to use (by allowing fibers code to be used in a project) with minor editing. Currently these packages have no other community place to go besides the atmosphere repo.





#TODO

# Mongodb addons

## Minimongo vs mongodb 

## Importing / exporting data   
  
## backups 
  
## Replication & database migration   
     

[TODO: rollbacks and database ?  What are the best practices in managing data when you rollback ?]

## logging you app and addons
 
??
heroku logs:drains              -- manage syslog drains


# Using multiple accounts for Heroku

  Sometimes you have one account on Heroku for billing purposes and another for developing applications with.  
  
  The simplest way to manage this is to create your apps with your billing heroku account and for each app you create you add the email address of your developer account as a collaborator.
  
  
  
  
## Hacking your project git config  

  A more technical approach to multiple accounts is to hack the git configuration in a specific project.
  
  In your ~/.ssh/config file, create a specific host definition for one of your heroku accounts, in this case we are creating a host for an heroku account used for billing (rather than app development)
  
    Host heroku.billing
      HostName heroku.com
      IdentityFile ~/.ssh/id_heroku_billing_rsa
      IdentitiesOnly yes
  
  Then edit the git remote url in your project **.git/config** file in your local repository for the project. Change the file to look like:

    [remote "heroku"]
      url = git@heroku.billing:<appname>.git

  The updated url should point to the host you have defined in the ssh config file and the app name is the usual app name that was generated by heroku create.

## Other Alternatives
* [Managing multiple heroku accounts](http://martyhaught.com/articles/2010/12/14/managing-multiple-heroku-accounts/)
* [Heroku accouts](https://github.com/ddollar/heroku-accounts)



# Using Private Git Repos
If your source code or dependencies are in a private github repository you can still use them.  You could use basic html auth but that would mean including your user name and password in the URL and would mean it can be seen by others.

With GitHub, you can use an OAuth token in place of using your actual username and password. If your OAuth token ever becomes compromised, it can easily be revoked.

git+https://<oauth_token>:x-oauth-basic@github.com/nsa/secret.git

You can easily create OAuth tokens/Personal API Access Tokens in your GitHub account: https://github.com/settings/applications4

https://help.github.com/articles/git-over-https-using-oauth-token


# Using Heroku Labs


# Heroku Clone

[Q: is this a lab or new feature ?]

  If you want to create a complete copy of an existing Heroku application, you can use the `heroku clone` command.

    heroku git:clone 


    
    heroku git:remote
    
  
  Cloning an existing app could be useful if you want to develop a similar app and use the existing app as a base.  You could also create an application template from which you want to create all your apps.
  
https://devcenter.heroku.com/articles/git-clone-heroku-app  


## Heroku fork

  Make a complete copy of an application, including the add-ons and data migration.
  
  

[Back to Workshop home](index.html)








<link href="index.css" rel="stylesheet" type="text/css">

# Using Mongodb

[Back to Workshop home](index.html)


<link href="index.css" rel="stylesheet" type="text/css">


# 12 factor app - creating scalable apps
 


[Back to Workshop home](index.html)








# Options on this workshop


* Adding Twitter bootstrap to the project to create some great UI designs for the site.  It will make the end result more interesting to talk about and allow some more creativity into the workshop.  See the [Twitter Bootstrap site](http://twitter.github.com/bootstrap/)


Other workshop ideas
--------------------
- Open Source project
  ¦-- using github for collaboration, pull request, using travis-ci for running tests with link to pull requests to know that they are safe to merge, using github for issue management, markdown for wiki, creating a markdown site on Heroku



Talks
-----
- polyglot developer, polyglot deployment - most developers are becomeing polyglot developers whether by design or neccessety.  With applications spreading over multiple server, devices, languages and technologies, often the most effective way is to use different tools for different jobs.  So what happens when it comes to deploy all this.  How do you manage to keep it all simple and part of the natural deployment workflow?

Enter the polyglot platform


PDF generation
--------------
Create a bash script that grabs the ruby gem and installs it, then calls the gem to generate the PDF




Resources

http://developer.force.com


forcedotcom developer user groups
http://bit.ly/fdc-dugs

Twitter accounts & hashtags
#forcedotcom
#askforce




In this chapter you will learn how to instantly deploy an application on Heroku using the Heroku Toolbelt.  You will also learn how to run the new application locally, make changes, and synchronize the changes with Heroku.  Then you will learn how to instantly scale your application, set configuration parameters through environment variables, and view your application's log entries.

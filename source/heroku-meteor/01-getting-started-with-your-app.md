# Chapter 1: Create a new application using Meteor

In this chapter you will create a small Meteor app using the simple command line interface. 

## Create a new Meteor application

You can use the `meteor` command to create a new application for you. 
  
When you create a new Meteor application, it creates a new folder with the name of the project you specified as part of the command.  So before running the meteor command, change to a suitable folder that is not already under version control or part of any other project, eg `~/projects`.   

Then use the command line to create a new Meteor application called *my-leaderboard* using the command:

    meteor create my-leaderboard --example leaderboard

In the above command we are using a meteor template called leaderboard so we get a basic application to work with.

## Running your Meteor app

You use the meteor command to run your application too.  So change into the new folder that was created for your project and run meteor:

     cd my-leaderboard
     meteor 

Your new application runs [locally](http://localhost:3000) and should display an interactive leaderboard.

## You meteor app source code files

The [Meteor leaderboard example](http://meteor.com/examples/leaderboard) we used to create the app is very simple, it consists of just three files

### index.html 
The main page, consisting of HTML markup and template code from the [handlebarsjs](http://handlebarsjs.com/) JavaScript library.

### index.js
The JavaScript code, including population of a [minimongo.js](https://github.com/meteor/meteor/tree/master/packages/minimongo) datastore

### index.css
Style definitions in standard CSS format

Part of Meteor is a JavaScript implementation of the MongoDB NoSQL database.  This holds the names and scores of people on our leaderboard.  This is changed to a MongoDB database when deployed on Heroku.

[Next](02-manage-your-project-changes-with-git.html)
[Back to top...](#top)
[Back to Workshop Home](index.html)

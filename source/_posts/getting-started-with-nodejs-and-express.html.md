title: Getting started with Nodejs and Express framework
date: 2013-08-19 15:12:00
categories: dev-tools
tags: 
- nodejs
---

{% img img-thumbnail http://4.bp.blogspot.com/-iCH8QV8CGAY/UgfW0SNj9bI/AAAAAAAAK3I/qE6rmyNEhOI/s1600/nodejs-logo-nodes.png %} 

[nodejs](http://nodejs.org/) is an important aspect in making JavaScript so popular for modern development and frameworks like [Express](http://expressjs.com/) make development with node more productive.  It is really easy to get going with [nodejs](http://nodejs.org/) &amp; [Express](http://expressjs.com/) and you can deploy your app live via [Heroku](https://www.heroku.com/) too.

<!-- more -->

# Express Framework

[Express](http://expressjs.com/) is a minimal and flexible node.js web application framework. You can easily create single & multi-page web apps or use it with other languages to build hybrid web applications. Express makes using node.js much less of a learning curve, although you can still get to the raw node power once you are ready. 

# Creating your first nodejs Express app

Assuming you already have nodejs installed ([install node on Ubuntu](http://blog.jr0cket.co.uk/2013/03/starting-nodejs-development-on-ubuntu.html)) along with npm ,the nodejs package manager, then you are good to go.

# Create your project

Create a folder for your application

    mkdir first-node-express

# Define project dependencies

Create a `package.json` file to define your project and its dependencies.  Express is treated as a dependency for the project and you simply specify the version of Express you want to include.

To see what version of express is available, use the node package manager to find out

    npm info express version

Edit the `package.json` file and define your project as follows

    {
      "name": "node-express-simple",
      "description": "A simple node express based website",
      "version": "0.0.1",
      "private": true,
      "dependencies": {
        "express": "3.3.5"
      }
    }

> the name of the project should not contain spaces


# Add libraries that Express and Node require

Now the project dependencies are defined, use the node package manager to pull down those dependencies from the Internet.

    npm install

You can view the dependencies of your project at any time by using the command:

    npm ls

# Create a simple route

In a text file called `web.js` define a simple route that will handle a request sent to the default address of your application, for example `/`. 

> You can call this file anything you like, but its often web.js, app.js or server.js

    // define a simple text response
    app.get('/', function(request, responce){
      responce.send('Hello nodejs express World');
    });

In the above example we are using response.send() to add a Content type and Content-Length to the response so they dont have to define them manually.

{% img img-code http://4.bp.blogspot.com/-iCH8QV8CGAY/UgfW0SNj9bI/AAAAAAAAK3I/qE6rmyNEhOI/s1600/nodejs-logo-nodes.png %} 

# Define a node server to listen to requests

In the same `web.js` file as above, add code to listen on a specific port and also send any logging information to the console from where your node app was run from.

    // bind to a port &amp; listen for connections 
    app.listen(3000);
    console.log('Node express app listening on port 3000');

> It can be useful to define a $PORT variable and use that variable in your code, especially if you use multiple environments like development, testing and production.  Also some platform as a service approaches provide a port variable on which your application must listen (eg. Heroku.com).

# Run the app locally with the node command

To run your application, use the command called `node` and pass it the name of the file your application is in.  In this case `web.js`.

    node web.js

You should see output on the console showing you that node is running and listening on the port you specified.

    Node express app listening on port 3000

You can now [open your new node express website](http://localhost:3000/).   You should just see the text messages displayed in your browser.

# Update your Node Express app code a little for Heroku

To make the application a little more robust lets make a couple of changes to the port it runs on and the logging message.

Edit the `web.js` file and change the `app.listener` code to be set by an Heroku environment variable (or default to port 5000 if no variable set).  The console log code is also changed to include the port the app is running on just to be sure.

    var port = process.env.PORT || 5000;
    app.listen(port, function() {
      console.log("Listening on " + port);
    });

We are also going to tell Heroku the process we want to run for our application, using a simple text file called `Procfile`

> the file name is Procfile without any extension and P should be capitalised, it should be in the root of your project folder.

Edit the `Procfile` and add the following line to run a web process using node and our application file.

    web: node web.js

# Add your project to a local git repository

I'm assuming you have Git already installed.  

> If you need to install Git, visit the [Git-SCM Website](http://git-scm.com/) or install the [Heroku toolbelt](https://toolbelt.heroku.com/)

Commit your code to your local git repository using the following commands:

    git init
    git add Procfile web.js package.json
    git commit -m "new project created"

# Create an Heroku application for deployment

Assuming your project is managed with git and you have an [Heroku account](https://www.heroku.com/) and the [Heroku toolbelt](https://toolbelt.heroku.com/), then you can simply create a space for your application on Heroku with the command:

    heroku create

This adds a remote URL for the git repository on Heroku that your application will be deployed from.  You can use `git remote -v` to check it has been added.

# Deploy your application to Heroku

Your code is managed by your local Git repository as one or more commits, so all you have to do is push those commits to Heroku and trigger a deployment.

    git push heroku master

# Start your application on Heroku

The final step to get your application running is to tell Heorku to run a process for your node server.  The following command will use the process defined in the Profile you created earlier.

    heroku ps:scale web=1

Now you can see your application running live on the Internet by navigating to the application address shown at the end of the deployment (URL) or simply type:

    heroku open

# In Summary

Creating a web app with Nodejs and Express is pretty quick and deploying on Heroku is easy, giving you a live app you can continue to build upon.

Next I'll look at doing more interesting things with Express, such as using it to generate an application skeleton.

Thank you.
[@jr0cket](https://twitter.com/jr0cket)


title: Starting Nodejs development on Ubuntu
date: 2013-03-25 14:37:00
categories: dev-tools 
tags: 
- javascript
- nodejs
- ubuntu
---

{% img img-thumbnail http://4.bp.blogspot.com/-bIFaJwok1vI/UVA3jCluB-I/AAAAAAAAJM0/-rtRbVUQ4no/s1600/Nodejs_logo_light.png %} 

**Outdated: please disregard this article as it is out of date.  I install node in my local filespace on Ubuntu now as its so much easier to manage.  Basicaly I download the Linux binaries and put them in ~/apps/nodejs/current, then add ~/apps/nodejs/current/bin to my path using my shell profile (~/.profile).  This makes using npm -g really easy and does not require the sudo command.**

[nodejs](http://nodejs.org/) is a very popular framework for JavaScript development, but as I found out at the [MongoDB hackathon](http://www.meetup.com/London-MongoDB-User-Group/events/106898042/)  its not that straight forward to get going.  So here is a quick guide to get going with Node.js on [Ubuntu](http://www.ubuntu.com).

<!-- more -->

## Installing nodejs on Ubuntu

Whilst there is a nodejs package in Ubuntu, it is version 0.6.9 and therefore quite a way behind the current version on the nodejs website.  So lets do a manual install with the latest version, 0.10.1.

> I since found an [alternative approach using ppa's](http://slopjong.de/2012/10/31/how-to-install-the-latest-nodejs-in-ubuntu/) but haven’t tried it out.

{% img img-code http://4.bp.blogspot.com/-WY7IRkhNpOU/UVA0m8Ly9cI/AAAAAAAAJMk/Sb1d7i8Mocs/s1600/nodejs-homepage-install.png %}

Download the install archive file and extract it.  I chose to do this in a folder called apps in my home folder.  Alternatively you could install it in `/opt/` or `/usr/local`

    mkdir ~/apps/nodejs
    tar zvxf node-v0.10.1.tar.gz

## Compile nodejs

As we are doing a manual install, we need to build nodejs to get the actual executable files.  This requires a C compiler on your laptop which is not installed by default.  So either use the Ubuntu software center to install the package `g++` or use the command line

    sudo apt-get install g++

To compile nodejs, first we run configuration to check all the neccessary external libraries are there and then we make node:

    ./configure
    make

## Adding node to your command path

Add the following to your environment in your `~/.bashrc` file (or `.zshrc` file if you are running zshell).  I moved the node executable file created by the compile process into a folder called bin, so I knew which was the right file to run.  Then I added that folder to the path.

    export NODEJS_HOME=/home/jr0cket/apps/nodejs/bin
    export PATH=$PATH:$NODEJS_HOME

I am using an environment variable called NODEJS_HOME as a convienience.  You can just add the whole path in one line.

## Installing NPM - the node package manager

{% img img-thumbnail http://3.bp.blogspot.com/-JJakqhflSfw/UVA4AMjSKAI/AAAAAAAAJM8/BbLzQXPlQbw/s1600/npm-logo.png %} 

The node package manager is a great way to get additional libraries into  your node projects.  It does not come with node itself, so you have to install it seperately.  Npm also needs node installed first.

On the node package manager website, the install process is defined as the following command:

    curl https://npmjs.org/install.sh | sh

In my manual install (not using Ubuntu packages) then node and npm are created in different folders.  So I put the npm executable file in the same bin folder I created previously for node, which I had already added that to the executable path.

Once npm is installed you can search for and install packages.  If you the `-g` option for npm install then the modules will be installed globally, otherwise any modules will be local to your project in an npm-modules folder.

Search for modules:

    npm search mongodb native

Install modules locally or globally:

    npm install mongodb
    npm install -g mongodb

## Testing out node locally

You can run an interactive session for nodejs (the node REPL) using the command:

    node

Then you can just enter JavaScript code and it is evaluated immediately.  You can also run code in files by using the command:

    node filename.js

So lets create a simple "Hello World" app for nodejs in a file called web.js

{% codeblock lang:js %}
var express = require('express');
var app = express.createServer(express.logger());

app.get('/', function(request, response) {
  response.send('Hello World!');
});

var port = process.env.PORT || 5000;
app.listen(port, function() {
  console.log("Listening on " + port);
});
{% endcodeblock %}

Running this with `node web.js` we get "Hello World" as the output.

## Testing out node on Heroku

nodejs is one of the languages supported on Heroku (a cloud service that gives developers a sane way to deploy and scale their apps).  Deploying this nodejs app on Heroku is therefore really trivial.

Heroku can usually work out what to do with many projects, based on the language and framework used.  However, just to be specific lets create a `Procfile` to tell node which is our entry point to our application.  In  this case we want node to start with the file `web.js`

    web: node web.js

Lets version the project with git

    git init
    git add .
    git commit -m "Initial project setup"

Then we can create an app on Heroku that we can deploy too - you will need an [Heroku account](http://www.heroku.com) and download the [Heroku toolbelt](http://toolbelt.heroku.com).

    heroku create

Heroku adds a new remote to our git project called heroku, so we can push our code to our app.

Now that our project is ready to deploy, lets push all the code to the  heroku application you created using git push, specifying the branch you are pushing (usually `master`)

    git push heroku master

Now open the node website in a browser using the URL given after the upload of your code via git push, or just the command

    heroku open

{% img img-code http://1.bp.blogspot.com/-m6l3bhlBB-Q/UVAoqU5PTeI/AAAAAAAAJMU/7OwfgCtBlTY/s1600/nodejs-website-helloworld.png %}

There is a nice [article about nodejs on heroku](https://devcenter.heroku.com/articles/nodejs) with examples of wiring node up to various data sources too.

## Learning JavaScript nodejs

Now for the fun part, learning how to program in nodejs and seeing how much JavaScript I can remember.  Here are some resource I found in the few hours I spent trying to learn about nodejs.

David Crockford has lots of great resources to help you write great JavaScript: 

* [JavaScript website](http://javascript.crockford.com/)
* [YouTube videos](http://www.youtube.com/results?search_query=crockford+on+javascript) 
* [Crockford on Javascript video series](http://yuiblog.com/crockford/)
* [NodeJS](http://nodejs.org/)
* [Node Package Manager](https://npmjs.org/)
* [Nodejs for beginners](http://net.tutsplus.com/tutorials/javascript-ajax/node-js-for-beginners/)
* [HowToNode](http://howtonode.org/) - community supported blog to teach fundamental concepts for writing effective code along with various other tips.
* [RequireJS](http://requirejs.org/) - optimising file and module loader for JavaScript, can combine all your code into one file for faster loading
* [Node-inspector](https://github.com/dannycoates/node-inspector) - Web Inspector based nodeJS debugger
* [Nodejitsu](http://docs.nodejitsu.com/) - a growing collection of node.js how-to articles from the community, range from basic to advanced.
* [Superhero.js](http://superherojs.com/) - a collection of articles, presentations and videos 
* [Nodejs google group](https://groups.google.com/forum/?fromgroups=#!forum/nodejs)** 
* [Suggestions of learning materials on Stack Exchange](http://stackoverflow.com/questions/2353818/how-do-i-get-started-with-node-js)

### Some semi-related links 
* [Setting up emacs as a javascript editing environment](http://blog.deadpansincerity.com/2011/05/setting-up-emacs-as-a-javascript-editing-environment-for-fun-and-profit/)
* [Webflow CSS3 playground](http://playground.webflow.com/)

Good luck with your JavaScript and node projects.

Thank you.
[@jr0cket](https://twitter.com/jr0cket)

# What is Heroku?

## Overview

Heroku is a service for developer to allow them to deploy any application easily, using the tools developers are already familiar with (build & version control tools).

Heroku is called a polyglot platform, because it supports many different programming languages and development platforms.  Heroku supports 6 of the most common languages (Ruby, Node.js, Java,Python, Scala, Clojure) and there is 3rd party support for approximately 50 other programming languages.


## Git Push Deploy

You can easily deploy your application using the version control system, Git.  A simple *git push heroku branch* will upload a copy of your code to Heroku, which will then use the same build process you used to develop with to build, deploy and run your code.

There is no propriatory code to add to your project.  Should you wish to add extra configuration on how your project runs, you can add them to a simple text file called the Procfile.



# Heroku alternatives

There are several other cloud services out there and more will come and go.

Because Heroku has made deployment a simple thing, it can lead people to believe that Heroku is easily replaced by, say, an AWS or Linode instance. If you choose to go that route, here are some aspects of managing your deployment you need to consider when taking that approch:

* logs - how to view and manage them in a consistent way.  What tooling do you have around the logs and can you seen causal relationships between events in different logs.
* disk space - how do you ensure that disk space is monitored effectively and your application does not grind to a halt due to a full drive, especially when scalling across multiple servers
* history of deploys and config changes
* rollback
* redundancy
* process management
* SSL termination
* reliability
* extra resources and services: databases, caches, sending/receiving mail, etc.
* access management
* scaling
* statelessness
* erosion resistance
* security (updates to base OS, language, framework, or at least targeted notices)

Heroku either makes these things non-issues or easy to achieve via the CLI.

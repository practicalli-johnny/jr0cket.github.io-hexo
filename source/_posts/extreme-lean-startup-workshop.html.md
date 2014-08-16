title: Extreme lean startup workshop
date: 2012-04-17 08:39:00
categories: agile
tags: 
- agile 
- clojure
---
{% img img-thumbnail http://clojure.jr0cket.co.uk/workshops/extreme-startup/extreme-startup-ninja.jpeg %}

[Extreme startup](https://github.com/rchatley/extreme_startup) is a practical workshop which simulates the excitement and insanity of working for a high pressure startup company, where every decision (or lack of) can make or loose you money - or in this case points!  

Lets delve deeper into the misteries of this kind of coding workshop.

<!-- more -->

Think of it as an extreme version of a coding dojo, where you are constantly challenged with new requirements and have to make quick decisions on what you should develop.  An extreme startup server is used to steadily grown requirements by asking you what seems to be simple questions at an increasing rate and complexity.  As these questions grow and change, just as a normal project would, you are continually driven to develop your code to meet these changes and keep earning points for correct answers.

# Extreme Startup - Leaderboard

{% img img-topic http://www.nilswloka.com/images/extreme-startup-2.jpg %} 

Scores are displayed for each time in real time, so you can see your progression in terms of your competition.  Teams can choose any language they wish to implement their product and there are a number of [basic project templates](https://github.com/bodil/extreme_startup_servers.git) to help you get started.

Teams will need to write an application that responds to HTTP GET requests and they should be prepared to parse some strings.  So the technical coding side is not the greatest challenge.

The challenge is knowing where to spend the time on your software solution.  Questions that are easy to answer initially will grow in complexity so the design decisions you make may become invalid quite quickly.

Like other dojos its best to run the extreme startup workshop with a number of pairs or very small teams, this makes sure that people are talking and involved in the decision making.

# Setting up the workshop

The facilitator of the workshop will setup an extreme startup hub server that will pump out questions and keep scores of all the answers.  

##  Extreme Startup hub

Install Ruby 1.9.2 (I suggest using [RVM](http://rubysource.com/installing-ruby-with-rvm-on-ubuntu/)) and get the [code from Github](https://github.com/rchatley/extreme_startup).

> Ruby 1.9.2 is available as an Ubuntu package

When testing the setup of the extreme startup hub, run the project using:

    WARMUP=1 ruby web_server.rb

When starting the extreme startup session, start up the server using:

    ruby web_server.rb

## Extreme Startup Company - 1 per team

Each team should create a project that will connect to the extreme startub hub and answer questions.  A team can used any language they like and there are a [range of templates](https://github.com/bodil/extreme_startup_servers.git) to get you started.

# Clojure based startup team 

If you decide to use Clojure for your product development you will need:

* Java runtime environment or SDK - openjdk 6 and 7 have been tested successfully
* Leinigen2 - to manage the build of your project
* Emacs + Clojure-mode, Clojure-test, paredit
* A REPL - using `lein repl` or `M-x clojure-jack-in` from Emacs

1) Download the example company web application templates from [Github](https://github.com/bodil/extreme_startup_servers.git) to give you a head start - you will need it, trust me!

    git clone https://github.com/bodil/extreme_startup_servers.git extreme-startup

2) Navigate to the Clojure project

Navigate to one of the Noir Clojure project folders (or try Composure) and update any project dependencies:

    cd extreme-startup/clojure/noir
    lein deps**
 
Have a look at the code, the `extreme-startup/clojure/noir/rules.clj` is the most important file at this point.  Hint: look at the `dispatcher` function and consider using the tests, you may need them for your sanity :-)

3) Load your code into the repl and fire up your browser

    lein repl

Running lein repl in the top level of the project directory should load the project code into the repl.  If not, then run

    (load-file 'src/extremestartup/server.clj)
    (server/start 3000)

3000 is the port number to run your server on, you can use anything that is available on your machine.  Open your browser at [localhost:3000](http://localhost:3000/) to see if it works.

4) Register your team as a player

The facilitator should provide you a URL to connect to.  Select the "I want to play!" link and register your team.

Check your current IP address on your laptop and use that address for the URL.  To find your IP address, open a command line terminal and run `ifconfig` (Mac / Linux) or `ipconfig` (windows).  Make sure you use the port number you specified, if different from above.

5) Get coding

Load the `rules.clj` file and extend the dispatcher function to your heart's content. Use the testrule macro to quickly unit test your dispatcher.

> Hint: you may want to have a look at the questions you are getting asked, so you can answer them!!

# Using a web server 

You can use `lein run` to fire up Jetty with your code - the only downside is you have to kill and run Jetty each time you make a change.  Jetty will run on port 8080 by default, so you would use that port value as the end part of the URL when adding a player - i.e. http://192.168.1.2:8080

# Clojure examples and experience reports

* [Bodil - StartupLoL](https://github.com/bodil/startuplol)
* [Nilswloka.com - Code dojo extreme](http://www.nilswloka.com/2011/08/17/code-dojo-extreme.html)

Thank you.
[@jr0cket](https://twitter.com/jr0cket)

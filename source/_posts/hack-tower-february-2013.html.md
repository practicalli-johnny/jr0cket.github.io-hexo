title: Hack The Tower - February 2013
date: 2013-02-22 14:08:00
categories: events
tags:
- hackday
---

{% img img-thumbnail http://3.bp.blogspot.com/-6h-4Dv2fnf8/USeAlY8lgwI/AAAAAAAAJFw/OQheQYOK8zs/s1600/tower42-surrounded-by-blue-cranes.jpg %}

When 100 developers and 1 robot signed up for the February edition of Hack the Tower, across many technical communities in London, I could tell it was going to be a big event.

{% blockquote @jr0cket https://twitter.com/jr0cket/status/300151177960628224 %}
Heading out for a full day of coding [@HackTheTower](https://twitter.com/HackTheTower) - excited about what people will create today #LSDC [#LondonScala](https://twitter.com/londonscala) #LJCjug #LdnClj #robots
{% endblockquote %}

Developers arrived from different communities, including

*   [London Scala user group](http://www.meetup.com/london-scala/)
*   [London Clojure community](https://groups.google.com/forum/?fromgroups#!forum/london-clojurians)*   [London Java Community](http://www.meetup.com/Londonjavacommunity/)
*   [London Salesforce developers](http://www.meetup.com/LondonSalesforceDevelopers/)
*   [London Software Craftsmanship](http://www.meetup.com/london-software-craftsmanship/)>


{% blockquote @balopat  %}
[@sandromancuso](https://twitter.com/sandromancuso "sandromancuso") Yeah our little team is awesome, I believe we're the last ones still coding :) [@HackTheTower](https://twitter.com/HackTheTower "HackTheTower") idea is great, I truly enjoy it!
{% endblockquote %}

<!-- more -->

# Starting the Hack day

Hack the tower is an open space where developers can collaborate on projects.

As the host I encourage people to form groups along share interests or goals, so they can learn things from each other and lean on each others experiences.  To that end, I ask anyone with a project or idea to share it at the start and encourage people to join one of these projets.  Most people had some idea of what they wanted to work on, although quite a few changed their minds when they heard about the robot project.

I spent part of the day working on Clojure projects, including setting up Clojure on Windows 8 (not known as great developer platform).  I also helped people get to grips with git and [managing multiple repositories](http://blog.jr0cket.co.uk/2013/01/git-log-makes-multiple-repos-easier-to.html) as well as a guidance on using [Heroku](http://www.heroku.com) and MongoDB for the London Scala website project.


# Cloud services powering Hack the Tower

{% img img-thumbnail http://1.bp.blogspot.com/-qlVcL6zWbjY/TzFMw8PPiGI/AAAAAAAAEbs/-Ozv0X_6mrQ/s1600/github-logo.png %}

Much of what we do at Hack the Tower is powered by cloud services for developers.  Without tools like Github, Heroku and Google search, coding applications would be so much harder.

We got a brief reminder of this when we broke Github :)
{% blockquote @balopat http://twitter.com/balopat/status/300232782590914560 %}
...and github is down for maintenance!!! :O [@HackTheTower](https://twitter.com/HackTheTower) [#LondonScala](https://twitter.com/londonscala)
{% endblockquote %}

Luckily Github was not down for long.  As git is distributed, we were able to save our changes locally or topped up on Coffee whist we waited a few minutes for Github to come back.


# Dancing robot, curious developers

Everyone’s instant favourite project seemed to be the NVO robot.  Its an amazing piece of kit.  Essentially a programmable robot that can by default can play Japanese music and do Tai Chi.

<iframe allowfullscreen="" frameborder="0" height="315" src="http://www.youtube.com/embed/rJnjmwtGQuE" width="420"></iframe>

You can program the robot visually, by dragging and dropping actions and wiring them up together.  You can create a sequence of positions and get the software to work out the moves necessary to go from one position to another.  Just like digital animators use in software like blender.

You can drill down into each of these actions and program the robot in python or several other languages.

{% img img-thumbnail https://pbs.twimg.com/profile_images/304321293/2442675643_5ffdd15b3b-square_bigger.jpg %}

{% blockquote @davesnowdon  %}
Many thanks to @[jr0cket](https://twitter.com/jr0cket) for organising [@HackTheTower](https://twitter.com/HackTheTower) today! Introduced a bunch of developers to [#NAORobot](https://twitter.com/NaoRobot), learnt stuff and had fun too
{% endblockquote %}

The robot has stereoscopic cameras and can do face recognition, in that it recognises a face when  it is in front of it.  This means the robot will talk to you when you when it looks at you, although it cant tell one face from another by default.  The robot has pressure sensors and fingers so it can interact with its environment.

{% blockquote @gnorsilva %}
[@HackTheTower](https://twitter.com/HackTheTower) [My view today](http://t.co/hfUIMWgT)
{% endblockquote %}

# London Scala user group
{% img img-thumbnail http://2.bp.blogspot.com/-kIrzG80xsL4/UMcqsNDxzzI/AAAAAAAAIsU/hKMCeoPdGkk/s1600/lsug-logo.jpeg %}

There were a lot of developers from LSug  group and they ended up split into three smaller groups to focus on different problems.

Some of the team were working with MongoDB, some working on the RSVP via meetup.  All the events displayed on the Lsug website can now be joined directly, without having to visit the meetup site.  Perhaps the total number of Yes RSVP's can be added to each meetup?

# Coding board

> [@villademor](https://twitter.com/villademor) Playing around with [codingboard.org](http://t.co/ReN3kzR5), [#Scala](https://twitter.com/scala") on [@HackTheTower](https://twitter.com/HackTheTower) [#LondonScala](https://twitter.com/londonscala) with [@balopat](https://twitter.com/balopat), [@gnorsilva](https://twitter.com/gnorsilva "gnorsilva") among others!

[Coding Board](http://codingboard.org/) is a small web application allowing developers to share code with each other in a hands-on session.  When we want to talk about the decisions we took as we approached a problem, its  nice to have the code itself shared on the screen in a syntax  highlighted way.

[Balint Pato](https://twitter.com/balopat) started this project as a [Christmas gift](http://blog.balopat.com/2012/12/a-gift-for-christmas-to-the-software-craftsmanship-community.html) for the [London Software Craftsmanship Community](http://www.meetup.com/london-software-craftsmanship/) using:

*   [Scala](http://www.scala-lang.org/) and [Scalatra](http://www.scalatra.org/)
*   [Twitter Bootstrap](http://twitter.github.com/bootstrap/) for the front end framework
*   [Selenium Webdriver](http://docs.seleniumhq.org/) and [ Specs2](http://etorreborre.github.com/specs2/) for "testing"
*   [Heroku](http://www.heroku.com/) developer cloud service for easy deployment
*   and no persistence whatsoever..:)

The project is under an open source license and the code is [available on Github](http://github.com/balopat/codingboard) for you to clone and fork.

{% blockquote @balopat https://twitter.com/balopat/status/300286147186282496 %}
we went live: Syntax highlighting on edit, max 24 hours long boards, loads of small fixes, altogether 10 pull requests! [@HackTheTower](https://twitter.com/HackTheTower "HackTheTower") [#LondonScala](https://twitter.com/londonscala)
{% endblockquote %}

Read [a blog of the days events](http://blog.balopat.com/2013/02/hack-the-tower-experience.html) for this project from Balint Pato himself.

{% blockquote @balopat %}
[balopat](https://twitter.com/balopat "balopat") [meetup photos](http://t.co/FX6Aqc8P) :) [@HackTheTower](https://twitter.com/HackTheTower "HackTheTower")
{% endblockquote %}

# London Clojurians - getting going with Clojure

{% img img-thumbnail http://3.bp.blogspot.com/-te_MuKdFBTQ/TzFLahe2BxI/AAAAAAAAEbY/Bn_JPN_s3qU/s1600/clojure-logo-500x.png %}

Two of us helped out a developer relatively new to Clojure, although they did have some past experience with Lisp.  We helped them get ther environment set up, which was a bit more of a challenge as the were running Windows 8.

Luckily its still fairly easy to set up a working Clojure environment on Windows, although just about every command seemed to ask for the Administrators password!  On the [Leiningen website](http://leiningen.org/), there is reference to a 3rd party bat file for getting going with windows.  The problem with this bat file is that its dependant on either wget or curl, neither of which were available on this machine.

We got round the problem by manually doing what the leiningen bat file did, downloading the .jar file and putting it in ~/.lein/self-install/...jar

A problem still remand with running lein.  The version in the .bat file was different from the ..jar file, so lein attempted to use and download a different version, which it couldnt find.  As we didnt have curl or wget to download the version in the bat file, we simply changed the bat file manually.

Some other aspects to setting up Clojure on windows 8 included:
- make sure javac is on the path, we only had java and lighttable failed
- install leiningen - there is a bat file or use cygwin
- install lighttable
- use lein to create a new project and connect to a REPL


# Salesforce for charity

{% img img-thumbnail http://2.bp.blogspot.com/-TF122Sgsv-4/UPxdX3gUFHI/AAAAAAAAI70/4WG-fXrH-yE/s1600/force_800x800.png %}

Another team formed around the [Salesforce platform](http://developer.salesforce.com/).  The were developing a tool to extract data from charity sites like Virgin Just Giving, helping fund raising organisations improve their fund-raising capabilities and getting a better view on where funds were coming from.

The data captured is filtered for the valuable data and the tool would allow you to match the incoming data with existing information you have.

The project is open source and [available on Github](https://github.com/stony-tsit/UK-Fundraising-Salesforce-App).

# Java, Java, Java

A team was also working on Java and some of the technical activity around the  Java Community Process (JCP).  The JCP is a way for others to help shape the future of the Java language and define the specifications for the language.

# Coding through the night?

{% img img-thumbnail http://2.bp.blogspot.com/-x6RUGJlfAto/USJUmLxp4BI/AAAAAAAAJEg/KEuS-PZUAZ8/s1600/london-by-night-from-the-tower.png %}

I did wonder at one point if we would still be here coding through Sunday as there were teams coding well into the evening.  By about 6pm everyone had got headed off into the beautiful London night.

> [villademor](https://twitter.com/villademor "villademor") [@sandromancuso](https://twitter.com/sandromancuso "sandromancuso") [@HackTheTower](https://twitter.com/HackTheTower "HackTheTower") [@balopat](https://twitter.com/balopat "balopat") [@gnorsilva](https://twitter.com/gnorsilva "gnorsilva") we really had a good time Sandro! Shame we couldn't catch up with you!

{% blockquote @sandromancuso https://twitter.com/sandromancuso/status/300283052507160576 %}
[sandromancuso](https://twitter.com/sandromancuso "sandromancuso") [@villademor](https://twitter.com/villademor "villademor") Seems you guys are having loads of fun. Shame I could not make it. /cc [@HackTheTower](https://twitter.com/HackTheTower "HackTheTower") [@balopat](https://twitter.com/balopat "balopat") [@gnorsilva](https://twitter.com/gnorsilva "gnorsilva")
{% endblockquote %}

# Join us for the next HackTheTower event

Come along and join the fun.  If you are a developer who likes to learn and share experiences with others, then all you need is a laptop and some enthusiasm (laptop optional).

Sign up at either:

* [London Salesforce Developer community](http://www.meetup.com/LondonSalesforceDevelopers/events/98334042/)
* [London Scala user group](http://www.meetup.com/london-scala/events/105841122/)
* [London Java Community](http://www.meetup.com/Londonjavacommunity/events/100797272/)

Thank you.
[@jr0cket](https://twitter.com/jr0cket)

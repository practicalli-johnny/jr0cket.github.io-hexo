title: clojure experience report january 2015
date: 2015-01-27 19:37:52
categories: clojure
tags:
- clojure 
---

## MixRadio - Mr Clojure 

  When creating a new service with a leiningen template to help bootstrap services
  
    lein new mr-clojure

##### Bootstrapping 
  bit difference from doing 4clojure problems and creating a more detailed service 
  
  First we answer out questions on "How do you start a jvm, connection pools, etc" and then put that learning in a standard form, the leiningen template.
  
Consistence - but not too much 
provide a way to make it possible for people to move between projects and still understand the basic approach that project has taken.  The template is not too big, so there is plenty of scope for people to come up with new idea and other good practices 

Some convienience scripts for running tests and test helpers to set up environment variables, etc

In an SOA getting your logs together takes effort, so the `resources/` sets up your logging in a consistent and valuable way.

scripts for making rpm packages - used for deployment (boo, no Heroku)

dependencies are the wite of the egg

this is the yoke
src/mr_clojure_example: setup.clj web.clj 

setup builds up connection pools, fires up graphite, embedded mongo views
web.clj - build up our routes 


problems 
- upgrading - no way to globally upgrade versions of libraries around all the different projects.  However, this problem has not manifested at all.

experience 
people are happy, books everywhere, an atmosphere of learning, feeding the fire of peolple and making it exciting to come to work.

More discussions are had around what they are are trying to do, rather than the constrained design decisions of hieracthy, classes, that need to change later anyway.

dev.mixrad.io 

##### Some references 
Clojure at Nokia - skillsmatter or QCon 

MixRadio dev blog 
Herding cattle at MixRadio
supercharging cyanite - tom Coupland




### Adopting Clojure at IOOF
@kornys
ThoughtWorks

IOOF - super annuation pension funds management 

typical stuff on the internet, transform, stuff in the backend 

client was very conservative, wanted to do it in java 
made the developers sad 

concurent set based engineering 
- building multiple stuff at the same time to see which works out the best 
- tried java, scala and clojure as the three approaches 
- 3 people on each team 
- each day one person was rotated to a different team 
- shared code each day, showcase - commented subjectively (was it nice) and objectively - how much did we get done 

subjectivelycoding testing problem solving changing requirements, etc

always discussed things in context 

in the first couple of weeks
- clojure was already ahead
- scala had issues around syntax
- java looked older 

objective time usage 

clojure spend most time writing code 
scala more time with libraries 

subjectively 
clojure started off as a challenge, but quickly got happier 
scala was all over the place 
java tanked, except for one good day, then tanked again 


1 scala, 1 java, the rest chose clojure 
the scala guy was weary that clojure would never take off 

in summary, clojure is awesome 

> soap library in clojure called neccessary-evil 

convincing others 

offered a free rewrite in Java if the clojure approach realised the fears they had
- thourghtworks figured it was cheaper to write the project in clojure and re-write it in Java, rather than write it in java in the first place

the clojure project was tiny compared to lines of code of the original system 10,000 compared to 700,000

there is more cost and risk in not changing that trying something new.

Clojure excelles when you are working with data, no need to continually construct artificial interfaces for data IO - types are very bad for working with data 


#### Blueshift 





Thank you.
[@jr0cket](https://twitter.com/jr0cket)

title: London Clojure dojo - 27th September 2011
date: 2011-09-27 23:59:00
categories: clojure
tags: 
- clojure
- coding
- events
---

{% img img-thumbnail http://ldncljdojo.eventwax.com/uploaded/logo//early-may-2011-london-clojure-dojo/20110419095837-ldncljdojo.png %}

As always the dojo started with a feast of pizza and drinks courtesy of ThoughWorks, the perennial favorite it seems with developers (I use it at my Scala dojos for the same effect).  A good turn out tonight meant the pizza went down quickly and we got onto the intros, with the monthly mystery question "If your names' not Bruce, what would it be" nicely stolen from Monty Python.

Here are the details of what happend at the dojo this time around.

<!-- more -->

Tonight's challenge was a children's classic - 20 Questions.  We set up a server to hold a expert system style data structure to help the teams play the game.  The challenge was two fold in playing the game in the first place and then adding to the question/answer data structure.

With enough people for 5 teams we split up into our groups and cracked on with the challenge.  Team two were using my trusty Lenovo laptop running Ubuntu, with the timeless classic emacs editor.  Emacs had the obligatory starter kick installed and the project was set up with Lein for the dependency management and Swank for the REPL.

Once we hooked up Emacs to the local swank server we were off...  well once we figured out what on earth to do first.

The challenges of a dojo are the blank project, what do we do first.  You either pontificate for a while, come up with 5 different opinions or if you are very lucky decide to jump at the first idea you have and crack on with it - knowing you will refactor it with in about 5 minutes - but thats the fun of the dojo...

Change is good... fast feedback is good... putting stuff in the REPL is a life saver...

To connect to the 20 Questions server we used the CLJ-HTTP library, pretty easy to use with simple get and put commands and a standard require statement for the library.  Adding the library to the project.clj and running lein deps brought down the relevant libraries and dependencies (just like a mini maven, but without half the Internet).

A few of different routes were quickly tried out but we quickly settled on an atom based data structure - as we were going to do updates to it.  We could have done something more elegant though this route was good enough for what we needed.

# Conclusion

Working in a tight knit group for about two hours working on a challenge is a very effective ways of exploring and getting a handle on a new language.  With a group of people who all have different ideas and experiences you take away a lot of things to think about.  I can see why people are driven to do more straight after a dojo and re-do the challenge in some of the different ways discussed.  I always get a great confidence boost for my clojure efforts, even though (or maybe because) I am far from proficient.

The code is up on GitHub for the world to see and its interesting to understand what a random group with a little bit of knowledge and [clojuredocs.org](http://clojuredocs.org/) can achieve in under two hours...</example>

Thank you.
[@jr0cket](https://twitter.com/jr0cket)

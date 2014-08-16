title: ClojureScript - the hard truth - London Clojurians March 2012 dojo
date: 2012-03-28 16:30:00
categories: events
tags: 
- clojurescript

---

{% img img-thumbnail http://4.bp.blogspot.com/-2cr1Ig4KeS8/T2DECGVqQbI/AAAAAAAAGKg/t8crLWDICgA/s1600/clojure-dojo-logo.png %} 

The March edition of the [London Clojurians](http://groups.google.com/group/london-clojurians) coding dojo all the suggested dojo challenges were to be carried out with  ClojureScript.  After a long list of ideas we voted to do either Conway's Game of Life or Monty  Carlo graphics.

Getting started with ClojureScript seemed reminiscent of the challenge the group faced a couple of years ago when first trying out Clojure.  Although getting started with Clojure itself is pretty easy these days, it feels like ClojureScript still has a way to go in terms of a great developer experience.

I looked at [ClojureScript One](http://clojurescriptone.com/) and was put off a little by the amount of git projects it was downloading as part of its bootstrap process.  I am sure its a great project, but seemed too much for the dojo and my netbook!

We settled on [lein-cljsbuild](https://github.com/emezeske/lein-cljsbuild) project and used the simple example that comes with it.  We fired the example up okay and had a working webserver thanks to some Ring Clojure magic and a tiny bit of JavaScript.

    lein deps
    lein ring server-headless 3000

Whilst we could display text in a web page and a JavaScript popup, we could not do anything that required working with the DOM - specifically setting up a graphic area or adding buttons.

In hindsight, perhaps we should have looked at the advanced example that came with lein-cljsbuild, although we would probably have also run out of time with that too...  

Perhaps if we had spent a bit of time before the dojo with the basics things would have gone better, however it was good to discover as a group the level of challenge involved and it made it easier to get started as we could draw from a range of experiences.

So what else did I learn?

# You need a JavaScript resource

I started to become a bit weary when it was mentioned that we should have someone in the team with JavaScript experience.  Even though we had someone with experience we still had lots of challenges.

# Google Closure libraries

{% img img-topic http://2.bp.blogspot.com/-qHb-QXI9CRY/T2HA8BHP6tI/AAAAAAAAGPA/H4kUBrgm6Vc/s1600/Google-developers-logo.png %} 

The [Closure Library](http://code.google.com/closure/library/docs/gettingstarted.html) is a JavaScript library that provides cross-browser functions for DOM manipulations and events, [AJAX](http://en.wikipedia.org/wiki/AJAX "AJAX") and [JSON](http://en.wikipedia.org/wiki/JSON "JSON"), as well as more high-level objects such as User Interface widgets and controls. 

The Google Closure library looks really great, but there seems to be a few challenges to get it to work with ClojureScript.  Again this is down to our limited time to get to grips with several APIs, so we had little luck finding something that worked.

# Where's my DOM

Our group got stuck on trying to find elements in the DOM via ClojureScript, repeatedly getting nil when asking for elements in the DOM.  We postulated that is was a timing problem, but were not able to code around the problem.

We fired up the [Chrome browser developer tools](http://code.google.com/chrome/devtools/) to see the errors, but couldn't get any of the many fixes we found on Google to work. 

# Using jQuery to load things up

By the end of the night I had a strong impression that you cant do ClojureScript without knowing a lot of JavaScript.  This goes against what I thought was possible, to write a Clojure style syntax that you could run inside a JavaScript engine.  Yes, I expected quite a bit of interop, having lots of doto calls to chain some JavaScript calls, but didnt figure on jQuery being there or so essential.

# Find an example that works

Find an example ClojureScript project that works and is easy enough to understand - without having to spend an hour setting up Leiningen plugins and dependencies or having to download lots of things from the Internet.  This was tricky to find in the time we had.

# Some blogs to and projects to review

* [Convex Hull ClojureScript demo - imagine27.com](http://jng.imagine27.com/articles/2011-07-23-101007_clojurescript_demo_convex_hull.html) 
* [ClojureScript sample apps](https://github.com/clojure/clojurescript/tree/master/samples)
* [Google Closure: How not to write JavaScript](http://www.sitepoint.com/google-closure-how-not-to-write-javascript/)
* [Google Closure: Getting Started](https://developers.google.com/closure/library/docs/gettingstarted)
* [Google Closure API documentation](http://closure-library.googlecode.com/svn/docs/index.html)

# In Summary

So first impressions of the experience suggest I need to read some good tutorials on the subject and review code of some more projects.  I plan on doing some more projects around Noir, so I'll try and see where the advantages of using ClojureScript are when using a set of Clojure web frameworks.

I am still excited about ClojureScript, but its one of those things where I need to find more time than I have to get to grips with it. If anyone has any other blog or project recomendations, please let me know.

Thank you.
[@jr0cket](https://twitter.com/jr0cket)

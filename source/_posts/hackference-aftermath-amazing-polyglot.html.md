title: Hackference aftermath - amazing polyglot conference
date: 2013-09-17 10:36:00
categories: events 
tags: 
---

{% img img-thumbnail http://2013.hackference.co.uk/img/hackference_logo.png %}

[Hackference](http://hackference.co.uk/) Birmingham was the first event I had been to that was both a conference and a hackathon.  Both parts excelled my expectations.  Its also the first big event I've been to in Birmingham outside the national exhibition centre (NEC) and the developers in Birmingham made me feel very welcome. 

This is a reflection of what happened at the conference part of [Hackference Birmingham](http://hackference.co.uk/).

<!-- more -->

# The Speaker line up

I described this as a polyglot developer conference as there were great talks from developers with backgrounds in PHP, Clojure, Javascript, Node, Java and Ruby.  There are many things that are common between languages, like good design, so its great to see ideas from such a broad spectrum.

> I may have taken some poetic license with my description of these talks.  This represents my interpretation of those talks and not necessarily what the speakers were actually saying!  Hopefully its close enough...

# Why don't you go out and do something less boring instead?

The opening talk by [Syd Lawrence](http://sydlawrence.com/) was very inspiring and a great way to wake up sleepy developers.  Syd encouraged us to _stop watching Coronation Street and try tech stuff out instead_.  Its easier than you think and there are lots of API's, tools and frameworks that make it even easier.  (the amount of hardware hacking in hackthons demonstrates how easy it is to get something working).

Its easy to make excuses not to try something new but every day it is getting easier and easier to try things out.  Over the last decade software development has truly become soft and malleable, so code is easy to change and using tools like Git its easy to change that code without hanging yourself.

In the last few years the same level of tinkering and malleability also applies to hardware.  With arduino &amp; raspberry pi kits along with tonnes of components its easy to build something with hardware and then pull it apart and build something else.  Electronics is after all a lego box of components for you to experiment with.

This encouragement from Syd reminded me of the BBC children's TV show from the past, [Why dont you?](http://en.wikipedia.org/wiki/Why_Don) which inspired me to go out and do fun stuff when I was so much younger.  Now I am older, why shouldnt I have just as much fun :)

# API Design - Give developers some love!

[Lorna Jane Mitchell](http://www.lornajane.net/) gave a run down of the do's and don't of API design. Having developed a number of API's herself you could hear the experience dripping from her words.

I cant do justice to her talk so I suggest you take a look at some of the quotes I pulled from her talk and if you like what you read then go and [buy her book](http://shop.oreilly.com/product/0636920028291.do?cmp=af-code-book-product_cj_9781449365080_7049572)... you wont regret it.

* HTTP has status codes, so use them to understand what is going on
* Content should be determined by header content type rather than URLs
* SOAP is great for Java/C# devs as they have a button that generates a SOAP service, hainving to  type a lot of XML is not nice
* REST is great but has "enthusiasts" that tell you your REST is wrong.  Taking a pragmatic approach to REST is better rather than trying to reach for perfection
* Build a heartbeat into your API, this provides a simple self help mechanism to check API is being used correctly by developers
* Consistence in experience will make a big difference when devs are choosing to use your API.  If your API is too erratic or unstable then you will loose your community. 
* Cache GET requests to help scale when you become popular.  Your API can use same principles as when caching static assets
* Handling errors is a measure of how good your API is perceived developers
* Tokens are so much nicer to use than a username/password combo for access control. OAuth2 is really nice to use now.

To me, the main point that Lonra Jane was getting across is that API designers need to engage with the community of developers to gain adoption and have a successful API.

# Getting Git and Github

Yours truly gave an impromptu talk about Git and Github, providing the audience a whole heap of tips and tricks to get the most out of these distributed version control tools.  For those just trying out Git for the first time, I created a [**Git quickstart guide**](http://jr0cket.github.io/developer-guides/git-quickstart-guide.png).

I also created a visual guide to Git and Github workflows:

{% img img-code http://jr0cket.github.io/developer-guides/git-and-github-workflow.png %}

The tips I shared included:

* using `git add` to help you be more selective in what you are committing without having to learn how to cherry pick

* using `git stash` to keep your work when you fall behind a shared remote (which I am sure we never do, right)

* configuring `git log` to be more valuable by showing a graph with repos, branches and tags (see my [.gitconfig file](https://github.com/jr0cket/dot-files-ubuntu/blob/master/.gitconfig) for examples of aliases used for git log and other useful short cuts)

I also talked about the workflow around Git and Github and encouraged people to keep it simple.  You can always add more to your workflow when needed, but jumping straight into something as involved as git flow may not give you the best experience.  When you are comfortable with git and are working on team projects, then take a look at Git flow and see if its for you.  There is [a good overview of Git flow by Jeff Kreeftmeijer](http://jeffkreeftmeijer.com/2010/why-arent-you-using-git-flow/).

# Boosting your JavaScript projects with Yeoman, Bower and Grunt

The ease in which a decent sized JavaScript project was created as part of the live demo in this talk by [Martyn Davies](http://hackference.co.uk/speakers#martyn-davies) has put this tool combo ([Yeoman, Bower and Grunt](http://yeoman.io/)) high on my list of new shiny things to try.  I had know about Yoman for a while although hadnt found the excuse to use it.  Now seeing all three tools working together (and me being a command line junkie) I will be using it for my [Heroku](http://www.heroku.com/) demos.  These tools give me a great way to go from scratch to continuous deployment of a live on the web app in less than 30 minutes

I can see Yoman, Bower and Grunt driving most if not all of my JavaScript app development, especially for [AngularJS](http://angularjs.org/).

# All the other great talks

I didn't see everyone's talk as I got into some great discussions with some of the speakers and developers attending the event.

I did managed to catch the [Clojure](http://clojure.org/) talk given by [Joe Littlejohn](http://2013.hackference.co.uk/speakers#joe-littlejohn) and [Mark Godfrey](http://2013.hackference.co.uk/speakers#mark-godfrey), speaking on how beautiful and powerful the [Clojure language](http://clojure.org/) is.  Its hard to sum it up in 30 minutes and even harder to share the experience without getting the audience to try the language out.  The guys did a good job to get the assembled developers interested.  If you want to know if Clojure is for you, then you can check out my eBook [Clojure Made Simple](http://developerpress.com/en/clojure-made-simple-introduction-clojure).

I talked to several other developers who were looking at Clojure too and I gave them ideas on [how to work with Clojure](http://jr0cket.co.uk/clojure).  I also helped out a few people with Clojure during the hackathon weekend.

# In Summary
Overall this was a great event and I came away felling I learnt a lot more from this conference because of the diversity than I did from very focused conferences like jQuery UK.

In my next article about Hackference Birmingham I'll [share my experiences of the Hackathon part of Hackference](http://jr0cket.co.uk/2013/09/25/hackference-aftermath-hacking-weekend.html/) and tell you about a word I have added to my vocabulary: "Hacklag".

Thank you.
[@jr0cket](https://twitter.com/jr0cket)

title: Hacked - a judges view of 500 developers creativity in London
date: 2013-07-26 17:40:00
categories: events
tags: 
- hackathon
---

As a judge at [Hacked](http://hacked.io/) I was amazed by all the developer talent concentrated into one weekend Hackathon.  There were lots of great ideas realised into apps in such a short space of time.  With 500 developer making up [74 teams](https://www.hackerleague.org/hackathons/hacked/hacks), it was a challenge to pick out winners. 

As Heroku were a major sponsor we decided to give out [prizes](http://hacked.io/almanac/heroku/) to 5 teams, even then it was still a challenge to choose only 5\.  We also gave out lots of swag and the t-shirts and moleskin notebooks went down a storm.

With so many diverse creations on show Hacked really lived up to its tagline: Learn ,Build, Share.

# Hacked.io: Learn

I ran a workshop introducing [Heroku](https://go.heroku.com/), a service to allow developers to deploy there apps quickly without worrying about complex scripts or managing servers.  There were lots of questions about Heroku, [Postgres](https://postgres.heroku.com/) database on demand and other [addons](https://addons.heroku.com/).  It was great to see enthusiasm from developers wanting to make the most out of the cloud.

I also ran a workshop on Git, so everyone could put their code up on Github or deploy on Heroku.  As Heroku uses Git for code deployments, then once you are comfortable with basics of Git, deploying in this way seems very natural.

[@neilmiddleton](https://twitter.com/neilmiddleton) also gave a workshop on the new Heroku API, allowing you to create apps, scale them and monitor them from your own applications.

The BBC, Nokia and lots of other sponsors also gave great talks and help with their APIs.  The BBC had a whole bank of TVs available to hack real TV apps on.

# Hacked.io: Build

Everyone pretty quickly got into teams to start hacking.  There were physical hacks, api hacks, music hacks, TV hacks and some really bizzar hacks going on all through the weekend.

When not running workshops, I interrupted teams hacking away to find out what they were up to.

The Heroku team had a few spare minutes free to build an app too.  Using the Heroku API, we built an app that would show a snippet of your logs when ever someone connected to one of your running apps, showing the location of the users IP on a map.

# Hacked.io: Share
It was great to get so many teams sharing their amazing creations.  The diversity of the crowd produced a feast for the eyes and ears.  I've only captured a few of my own highlights in this post.

# Getting Organised

One of the apps I liked the most was the **Event board for organiser** by [@EChesters](https://twitter.com/EChesters) as running developer events on the scale of Hacked is a big challenge.  The Hacked team did very well, although having a good app to managing all aspects of an event in real time would help any team run a event more smoothly.  I especially liked the real time alerts mobile app.  Lets hope this team takes the app further.

{% img img-topic http://3.bp.blogspot.com/-SBMbodpj9fE/UfKrfRx_7rI/AAAAAAAAKwA/f4muQ-9xtfw/s1600/hacked-machines-3d-printing.png %}

# Rise of the Machines

There were many hardware hacks at the event, especially with [node copters](http://nodecopter.com/), micro node copters, nano node copters and copters controlled by Playstation Move controllers.  My favourite amongst these was Wild thumper, a node copter that could follow a remote controlled car just by attaching a small ring of lights to the car, that was really cool.  [Arduino](http://www.arduino.cc/) powered controller for remote controlled car, with [Raspberry Pi](http://www.raspberrypi.org/) camera driving the copter.

# The world needs more cuteness

There were cute hacks like the [Bunzor Cam](http://tiny.cc/bunzorcam) by [@danielknell](http://www.twitter.com/danielknell), [@mfujica](http://www.twitter.com/mfujica), [@motoko_k](http://www.twitter.com/motoko_k) and fudge the rabbit, because there are just not enough cute bunnies on the web.

Other cute hack involved a knitted darlek and a chrome extension that changed any pictures on a web page to that of a cat... great fun if you do a Google image search for dogs and watch them all change to different cats!

{% img img-topic http://1.bp.blogspot.com/-F6AIhd1p1xY/UfKozY_9lKI/AAAAAAAAKvk/WjFnAnVpZ64/s1600/philps-lightbox-wires.png %}

# Let there be light

It seems the Hue Light boxes from Philips caught a fair bit of attention.  These were a 3 bulb array that you could connect to over WiFi or Ethernet and control the colours and sequencing of the lights.  The most useful hack for me was the BusBulb.  This hack tapped into Transport for London open data on transport and gave you a lighting countdown to when you needed to leave for your bus.  This would save me a lot of checking of my phone for the time and save batter.

# The Hacked.io Hackathon Winners

It was tough deciding on winners when there were so many great submissions to choose from.  I spent time finding out what the teams were building as its hard to get a true picture just from the 90 second demo at the end.

There was one app that all the judges quickly agreed was the winner, FlashMed.  This app was quite simple but provided a very important service, managing a medication regime for the elderly.  Most elderly people have to take a range of medicines and these are all colour coded to help them.  However its easy to forget the schedule you need to take.  So the app connects to a Phillips Hue lightbox and displays the colour of the medication at the time you are supposed to take it.  Once you have taken it then the light will switch off.  If you fall asleep then the light shows which medications you need to catch up on.  Simple and effective

The peoples choice went to the crazy kids who won two giant lego Starwars kits, the death star and millenium falcon.  That should keep them busy next weekend.

# The Heroku Winners

{% img img-topic http://2.bp.blogspot.com/-Aa5-sCTus4w/UfKpnTsSMlI/AAAAAAAAKvw/sIbH0AMTxy4/s1600/hacked-prizes-heroku-excitement.png %} 

# [API Unifier](https://www.hackerleague.org/hackathons/hacked/hacks/heroku-api-using-restapiunifier)

[@theNeomatrix369](https://twitter.com/theNeomatrix369) created a wrapper around the Heroku API to help Java developers create cool applications easily with the Heroku API.

The API Unifier is a lightweight Java library that brings together a collection of RESTful APIs under one roof!  This simplifies the use and maintenance of dependencies on external APIs. This library creates an abstraction layer between your application and APIs from disparate vendors to increase cohesion, reduce coupling.</div><div>

# [MusicMatch.io](https://www.hackerleague.org/hackathons/hacked/hacks/musicmatch)

MusicMatch is a social music competition where you need to guess the correct 10 second clip to build up points to get you up the leader board.  The quicker you answer the more points you get, but get the answer wrong and you and you lose points.

The application was developed with Nodejs and uses Nokia music API to get the music tracks.  Redis (Heroku addon) is used to manage the leader board and the app was deployed on Heroku.

# [Boomerang](https://www.hackerleague.org/hackathons/hacked/hacks/boomerang)

This app is a really fun idea and adds a different dimension to the experience at an event.  With Boomerang you take a picture and throw it out there and see what picture you get back in return.  You never get your own picture back, so you get to experience a little of what everyone else at an event experiences.

The team built this as a native android application with a back-end service running on Heroku to manage which images you received.  The app could also be passed to your friends or strangers at the event if they have a NFC enabled phone.

# 99hours

This app helps people develop their ideas and get thought the barriers to turn those ideas into apps.  99hours connects people with those ideas  to those who can help them out.  The goal is to create a highly collaborative place to nurture ideas into projects.  This collaboration is realised in features such as feedback from the community on ideas by up-voting, or providing a variation on the kick-starter model and allowing direct donations to a project you want to support.

# Pigeon

Tom Morris created an app called pidgeon as a kind of location brokarage service, a personal api for your location.  Deployed on Heroku, this app has a simple API to post location information into forsquare to give real time updates of where you are.  To display map information on the website, the hack was written using Rails and used MapBox, OpenStreetmap and MogoLab Heroku addon.  Sometimes you want to hide your location, so the app also had rules to hide your location when you are at home or other personal locattions.  To test the app, Tom also used Macosx controlPlane to simulate different networks.

# The Next Hackathon

It does take a few days for the adreneline and lack of sleep to balance themselves out after a Hackathon.  Lucklly then there is a few weeks before Leeds Hack.  Leeds hack is great, especially if you want to get your children involved in coding.

I'll be at Hackference Birmingham next, the first event of its kind in Birmingham, so it should be a great event.  I'll be doing workshops around Heroku &amp; Git and it seems there is lots of interest around Clojure, functional programming on the JVM. 

{% img img-topic http://si0.twimg.com/profile_images/3687034314/640a734aa1b7d887be40fedac191679f_normal.jpeg %}

{% blockquote ukmadlz https://twitter.com/ukmadlz/status/359011375110045696 %}
Mike Elsmore - I cordially invite everyone who went to [@HACKEDio](https://twitter.com/HACKEDio) to come to [@hackferencebrum](https://twitter.com/hackferencebrum) and help me make something awesome [http://hackference.co.uk](http://t.co/8lvxK8Qa9e "http://hackference.co.uk")
{% endblockquote %}

Thank you.
[@jr0cket](https://twitter.com/jr0cket)

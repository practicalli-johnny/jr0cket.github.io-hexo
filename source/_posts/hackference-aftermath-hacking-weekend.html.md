title: Hackference aftermath - hacking the weekend for fun & prizes
date: 2013-09-25 02:03:00
categories: events
tags: 
---

{% img img-thumbnail http://2013.hackference.co.uk/img/hackference_logo.png %}

I've added a new work to my vocabulary: **Hacklag**.  Hackference Birmingham left me totally exhausted and yet once I had recovered I was highly motivated to try the things I had experienced there.  So I am sharing my experiences from the weekend hackathon of fun, discovery and glorious food.

> Previously I [shared my experiences of the Hackference polyglot conference](http://jr0cket.co.uk/2013/09/hackference-aftermath-amazing-polyglot.html), detailing what I learnt from the great talks there.

<!-- more -->

# The Hackathon weekend

{% img img-thumbnail http://bean2bed.com/skin/frontend/default/bean/images/slide/4.jpg %}

The venue at Boxxed had a great open space that encouraged people to collaborate and provide an open and friendly workspace.  There was plenty of table space, huge bean bags that turned into beds and sofas to lounge in, not that many of us took the time to lounge until the early hours of Sunday morning!

We started Saturday with some overviews of API's and developer tools from the sponsors of the Hackathon, including [Pusher](http://pusher.com/), [Heroku](http://www.heroku.com/), [Twillio](https://www.twilio.com/), PayPal, Paymill, CloudFoundry and a few others.  Each sponsor also described what prizes they had on offer.  With a trip to their offices in Berlin, [SoundCloud](https://soundcloud.com/) had arguably the best prize on offer.

# Food glorious food

{% img img-topic http://1.bp.blogspot.com/-ph9Hh_m30S0/UkIcY1ioJWI/AAAAAAAALo4/0OGMV8JqrM8/s1600/20130901_122932.jpg %} 

During the day there was delicious food on offer and plenty for everyone.  A good job as I didn't get round to eating anything on conference day, unless you count a pint of Guinness as food :)  I really enjoyed the curry of the Saturday evening and I also had a few cups of curry to keep me going through the night as there was a bit left over. 

# Friendly, collaborative developer crowd

I met lots of great people at the event and I think I spoke to everyone there, it was a very friendly event.  Some of the developers were quite experienced and some were relatively new and some were quite young and will become the future of our developer communities.  Everyone got involved and seemed to have learnt a lot over the weekend.

# My favourite hacks from the event

{% img img-code http://2.bp.blogspot.com/-D5BN3ESCXNA/UkIf2EzBQ1I/AAAAAAAALq8/HwZZJdXtU0I/s1600/20130831_164207.jpg %} 

There were some great ideas on the go during the hackathon, some that were perhaps a little too ambitious but great to see anyway.  There were over 20 hacks on show at the end and as Mike asked me to be one of the judges, it was a challenge to choose the most deserving hacks after everyone had put so much effort into them.

This is a top 5 of my own favourites from the hack, not the actual winners (although there is some crossover).

## 5 - HackSocNotts

I've met the team from HackSocNotts at a few hackathons now and they are a really enthusiastic and creative bunch.  This time they were building a visual hack that would be a light-show at this years freshers fair, demonstrating how much fun you can have if you join in.

The team assembled a strip of 32 LEDs all wired up to an [Arduino](http://www.arduino.cc/) board and controlled by a Raspberry Pi.  The aim was to allow anyone to set up a pattern with the lights via a simple website, making it very interactive.  The hack consisted of two node programs communicating over web-sockets, firing codes into the register of the strip.  The website was a simple Twitter bootstrap affair.  The biggest technical challenge was working with node and the LED hardware, but eventually they got it working some time in the middle of the night.

## 4 - Uber hack

{% img img-topic http://blog.uber.com/wp-content/uploads/2011/12/New-Logo-Vertical-Dark.jpg %}

Uber is a taxi ordering service which you can use from your mobile phone.  You can see where the available cars are in your area.  What the Uber team managed to do is reverse engineer the Uber API so they could track their fleet of cars from anywhere in the world.  By entering a location in their web app, the Uber cars were shown on a Google map.  It was a great app and a very slick presentation, very surprising since the team consisted of a 19 year old and a 16 year old.


## 3 - Code Tennis

Created by [Andrew Nesbitt](https://twitter.com/teabass), [Code tennis](http://code-tennis.herokuapp.com/) is a fun way to improve your skills with Git, especially when it comes to working with Git as a team.  In the game you can be as Machiavellian as you like, thinking of commits that will actively cause your opponent more of a challenge when merging your commits to their local repository and pushing those commits to the shared Github repository.

{% img img-code http://3.bp.blogspot.com/-dM2mTiykXzA/UkIWKc_eVyI/AAAAAAAALks/vZBSA1YB-jY/s1600/code-tennis.png %}

The game involves each developer taking it in turns to push code to a shared repository on Github.  A `git push` flips the access to the Github repository to the other player, so you have to take it in turns.

However, whist waiting for your turn to push you can make local commits.  Deciding on what to commit and how much of a challenge you can make for your opponent will help you understand how much you really know about the power of Git.

All changes pushed to the shared Github repository get automatically published onto Github pages.

The name "Code Tennis" comes from the gamification of image creation by graphic designers.  They play Layer Tennis where each graphic designer takes it in turn to create a graphic on one layer of an image.  Each turn adds another layer to the image by those playing the game to get an interesting mix of styles and very different end results.

As with graphic designers, playing code tennis get helps you discover different ways of using Git repositories in a fun way.  Hopefully you will use these new skills for the benefit of your team :)

# 2 - Distributed speakers

{% img img-thumbnail http://www.iainclaridge.co.uk/blog/wp-content/uploads/munny_speakers.jpg %} 

Using Twillio, [Syd Lawrence](http://sydlawrence.com/) set up a simple website that that streamed sound to any mobile that called a particular telephone number.  Syd got a whole bunch of use to call the number and within a few seconds we had all become a distributed speaker system, blasting out Rick Askley!

It was a simple idea that made good use of an API to get the hack done.  It also reminded me of fun things done by seb.ly with graphics and audience interaction.

As Syd was also judging then we couldn't give him a prize (he wouldn't accept one anyway).  I hope that if he takes it forward then it is used for other songs that Rick Askley

# 1 - Super pirate battleships 

This was an amazing hack.  The team built a fully working game that looked really good and worked very well, they also made the game environment dynamic.  Their game pulled a music track from SoundCloud and as it played the track was analysed and the pattern of the soundwave was used to determine where obstacles and power-ups should be placed during game-play.

{% youtube 6rJqpdJffac  %}

Top prize winner: Super Pirate Battleships video cortesy of [Mark Jolley](https://twitter.com/J0lley))

# In Summary

There were lots of really great hacks I havent mentioned and so would just like to thank everyone for there hacks and making it a really entertaining and enlightening weekend.

You can see more of the hacks by looking at some of the [videos from Mark Jolley](http://www.youtube.com/playlist?list=PLsTreukqJm95hm0VQD4QWITpFKISaX_l_) of the hack showcase, or visiting the [Hackference page on Hacker league](https://www.hackerleague.org/hackathons/hackference/hacks).  If you are not at work and feeling brave you can even check out [Syd Lawrences' twerking Video](https://www.dropbox.com/s/obbsb367qorijw0/syd-twerkin.mov) or the great photos from [Andy Piper](http://www.flickr.com/photos/andypiper/with/9628126743/) and [myself](https://plus.google.com/u/0/photos/117080433375668558463/albums/5927331270432594721).

I really hope Mike runs Hackference Birmingham again as I had such a great time.  Hopefully he will get more volunteers to help him next time as he did a huge amount of work to make this all happen.  Thanks Mike, you did a fantastic job.

Thank you.
[@jr0cket](https://twitter.com/jr0cket)

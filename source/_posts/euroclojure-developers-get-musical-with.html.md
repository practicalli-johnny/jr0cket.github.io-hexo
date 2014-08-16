title: EuroClojure - developers get musical with Overtone
date: 2012-05-24 11:02:00
categories: events
tags: 
- clojure
- euroclojure
---

{% img img-thumbnail http://1.bp.blogspot.com/-Wo6T3gjQpAA/Tzeu0e4laKI/AAAAAAAAEeQ/xbyWBx246qc/s1600/overtone-logo-rounded-corners.png %} 

Sam Aaron and Jeff Rose gave a whirlwind tour of creating music with Overtone, an open source music generator written in Clojure. 

You can define your own instruments, map keyboards and other synthesiser hardware, all to make some funky sounds - although you probably want to have headphones on when experimenting!

> [@samaaron](https://twitter.com/jr0cket) with overtone you can sit on a train and make musicI had fun creating my first overtone project from scratch at the last Overtone Hackday.  Have a look at [how I set up my environment](http://jr0cket.co.uk/2012/02/developers-making-music-together-london.html).

# The Design of Overtone

{% img img-topic http://1.bp.blogspot.com/-zi_tjIry5n0/TzetrkxV1XI/AAAAAAAAEeI/CVhhVWK-oHM/s1600/overtone-logo.png %} 

Music is not a very easy concept to define in software.  Typically you start with a synthesiser and work your way up to notes and chords.  Eventually you may get to a music piece, but this is often driven by a hardware keyboard and recorded.

The difficulty is that everyone has a different idea of how to describe music.

Overtone comes in two parts.  The Super-Collider generates all the sounds from over 500 midi building blocks, essentially you create a directed graph that returns values to represent those sounds.  The clojure project part allows you to define instruments (synthesisers) and orchestrate these instruments together.

# Basic approach to making music

Overtone generally works on the principle of subtractive synthesis.  You create a number of different sounds by defining individual instruments and by adjusting the time and frequency of the sound wave to vary the sounds produced.

Once you have some instruments, then adding an envelope generator will give you a changing sound through time by, essentially multiplying the sound by the envelope.

Join sounds together by creating a player function that takes a time and plays the instruments - adding durations to the sound.  

To spice up your sounds you can then experiment with playing two different frequencies at the same time, referred to as multi-channel expansion.  A resident low pass filter is also fun to experiment with.

{% img img-topic http://3.bp.blogspot.com/-0rI8wFPDhPA/T74BOseE1RI/AAAAAAAAIEM/eIjoBNil-bk/s1600/twiki-from-buck-rogers1.jpg %}

Sam and Geoff showed off what they call _the stepinator_, which seems to emulate a square wave form which steps through a series of values over time.  This created some Buck Rogers style music.

{% img img-topic http://2.bp.blogspot.com/-VkwWleTTwuI/TzfwcibV8QI/AAAAAAAAEeY/uwjAdgtY3dw/s1600/novation-launchpad-music-control-surface_1.jpg %}

Eventually you will want to use an external keyboard or some hardware device to pay your music as calling functions over and over again from within the REPL will only get you so far.  If you map functions, frequencies, etc to the external player controls then you can play your clojure code..

# Getting Visual

{% img img-topic http://2.bp.blogspot.com/-NmIbHt43IE0/T74EEoWjzcI/AAAAAAAAIEY/VPDM_0NLrMs/s1600/overtone-graphics-samaaron.png %} 

To make the music come alive even more, you can use the [Java processing framework](http://processing.org/).  Instead of calling processing directly, you can use the clojure project [Quil](https://github.com/quil/quil) to visualise the overtone sounds, creating a sphere and controlling the size of the sphere with the different frequencies of the sounds.

# Get collaborative

{% img img-topic http://3.bp.blogspot.com/-ZvjBQPJ0xFc/T74F49jxpAI/AAAAAAAAIEg/UwD1s9smJFE/s1600/freesound-logo.png %}

Sam and Geoff are trying out different ways of sharing the REPL so they can jam together.  Many people are sharing their sounds on [freesound.org](http://freesound.org/), a collaborative database of Creative Commons Licensed sounds. Browse, download and share sounds

# Get started

Read the [Overtone documentation](https://github.com/overtone/overtone/wiki) to get started or have a look at [my setup on Ubuntu](http://jr0cket.co.uk/2012/02/developers-making-music-together-london.html).  Dont forget to experiment.

Thank you.
[@jr0cket](https://twitter.com/jr0cket)

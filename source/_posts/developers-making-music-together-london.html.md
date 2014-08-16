title: Clojure developers making music together - London Overtone Hackday
date: 2012-02-12 20:17:00
categories: events
tags: 
- clojure
- overtone
---

{% img img-thumbnail http://4.bp.blogspot.com/-giXovBlzXbs/TzeoJug54wI/AAAAAAAAEd4/6yUK0y8UnDk/s1600/snow-music-wobble2.png %} 

The coldest night in London of 2012 so far was the warm up to a symphony of music by a collection of unstoppable Clojure hackers. As it was my first hackday with Overtone there was lots of new things to learn, from setting up the environment to a whole load of interesting music theory.

I also have [Gnossiennes No.1 by Erik Satie](http://www.youtube.com/watch?v=RyFhsG8Ip4E) on an endless loop in my head after having fun playing around with a piano synthesiser.  

{% img img-topic http://2.bp.blogspot.com/-AIEshRHUGJY/TzeoeMtSQ2I/AAAAAAAAEeA/7B8Zn412rR0/s1600/rolf_harris_stylophone.jpg %}

I cant really cant do justice to how much fun it is working with Overtone.  Its like getting your hands on a [Stylophone](http://en.wikipedia.org/wiki/Stylophone) for the first time, just after seeing Rolf Haris demo it on TV! The only difference being you can make much better music with Overtone.

There is something just so ultimately geeky and fun in creating music using a functional programming language like Clojure.

I first tried Overtone at a London Clojurian coding dojo and with the help of the rest of the team we were quickly creating weird and wonderful sounds - although not quite in the same leaguge of 

{% img img-topic http://1.bp.blogspot.com/-Wo6T3gjQpAA/Tzeu0e4laKI/AAAAAAAAEeQ/xbyWBx246qc/s1600/overtone-logo-rounded-corners.png %} 

Thanks to some great [documentation on the overtone github site](https://github.com/overtone/overtone/wiki/Installing-overtone) it was pretty easy to set up my [lubuntu](http://lubuntu.net/) laptop with an audio server, Overtone server  and a nice lightweight clojure development environment (emacs,  leiningen).  I am afraid it will take me a bit longer to absorb music theory!

# Setting up the audio for Overtone

In order to get sounds out of your overtone project on Linux, you need to add a few packages.

    sudo apt-get install jack-tools ant openjdk-6-jdk fftw3 qjackctl

As you grow your overtone project you may want to switch to a linux kernel set up for real time processing, but to start with this is not necessary.  If you do get more involved projects, its probably a good idea to also look at [Ubuntu studio](http://ubuntustudio.org/) which provides a great selection of audio, video and graphics tools. 

_Mac OSX already has a suitable sound server, so nothing extra is required.  If you are using windows, overtone is supported also (not sure if you need to set anything up though).

# Create a new overtone project

{% img img-topic http://1.bp.blogspot.com/-rxD8__T6tzA/TzFNNTKKLwI/AAAAAAAAEb8/k10iLxa3I70/s1600/leiningen-face.jpg %} 

An [overtone project](https://github.com/overtone/overtone/wiki/Installing-overtone) is just like any other clojure project, with the overtone dependency added.

Create a new clojure project with your build management tool of choice: [maven](http://maven.apache.org/), [cake](http://clojure-cake.org/) or [leiningen](http://github.com/technomancy/leiningen).  I used leiningen as my tool of choice. 

    lein new tutorial

Add the Overtone dependencies to the project configuration file `tutorial/project.clj`

``` tutorial/project.clj 
(defproject tutorial "1.0"
  :dependencies [[org.clojure/clojure "1.3.0"]
                 [overtone "0.6.0"]])
```

With the overtone dependencies added to the project file, used leiningen to download the jars that make up overtone itself.

    lein deps

Leiningen will download about 16 jar files for overtone 0.6.0 and places them in the project lib folder.  This gives you all the libraries you need to start creating things in overtone, including an appropriate version of clojure.

# Fire up your environment

Emacs not only has great support for the Clojure language, its a great way to try out your code by evaluating individual functions (s-expressions).

My preferred way to launch emacs is to change directory to the project top level and fire off emacs with the project file

    emacs project.clj &

Using the dynamic environment of Clojure, the REPL, is a great time saver for trying out functions as well as running your project code.  To fire up a repl inside emacs I use the new emacs 24 approach, running `Meta-x (clojure-jack-in)` to start up and connect to a repl using the underlying lein project file.

    Meta-x (clojure-jack-in)

I have set up a keyboard shortcut of `C-c C-j` to make this even easier.

# Starting Overtone
{% img img-topic http://1.bp.blogspot.com/-Wo6T3gjQpAA/Tzeu0e4laKI/AAAAAAAAEeQ/xbyWBx246qc/s1600/overtone-logo-rounded-corners.png %} 

For my initial experiments I run an overtone server on my laptop, that way I can also play on the train home.  You can also use an external overtone server called the [SuperCollider](http://en.wikipedia.org/wiki/SuperCollider) (no not the [LHC](http://en.wikipedia.org/wiki/Large_Hadron_Collider))

In the repl, I fired up the internal server (dont try to fire off both servers in the same repl, it crashed my repl)

``` Overtone in the REPL 
(use 'overtone.live) 
          _____                 __
         / __  /_  _____  _____/ /_____  ____  ___
        / / / / | / / _ \/ ___/ __/ __ \/ __ \/ _ \
       / /_/ /| |/ /  __/ /  / /_/ /_/ / / / /  __/
       \____/ |___/\___/_/   \__/\____/_/ /_/\___/

                          Programmable Music. v0.6

Hello jr0cket, may this be the start of a beautiful music hacking session...
nil
``` 

# Defining my first instrument

I soon discovered that it does take a little time to build your instruments.  Its like any good programming challenge, there are many ways to do things and there are always lots of surprises.  Reading the [getting started guide](https://github.com/overtone/overtone/wiki/Getting-Started) helped me with my first instrument.

```
(definst annoying-tone [] (saw 220))
```

This is a simple and rather annoying tone that uses the saw function to create the sound. To play the sound I simply call its name:

```
(annoying-tone)
```

The easiest way to end your experiment in sound quickly is to use the `(stop)` function.

# Quickly testing out your instruments with emacs

{% img img-topic http://1.bp.blogspot.com/-PLeobToC6lc/TzFJCfBSLPI/AAAAAAAAEbE/zSx1cOgHzZE/s1600/emacs128x128icon.png)</div>If you compile the clojure file in emacs you can then evaluate your s-expressions (functions) using a keyboard shortcut.  To compile the clojure file, select the buffer in emacs and use the keyboard shortcut `C-c C-k`

If the file is not saved, you will be prompted to confirm if it should be saved.  Once  successfully compiled, move the cursor to the end of the s-expression  you want to evaluate - after the last closed parens - )

Evaluate the pre S expression with the keyboard shortcut `C-x C-e`

To stop the evaluation, switch to the repl and use the `(stop)` function.

# Define an emacs macro to quickly stop the music
 
So you dont have to keep switching backwards and forwards between the repl, define a keyboard macro for the stop function.

`Meta-x (start-kbd-macro)` or you can use the keyboard shortcut `F3`

Use the mouse to enter the repl window and type your function / macro, in this case typing `(stop)`

`Meta-x (end-kbd-macro)` stops additional mouse and keystrokes being added or use the keyboard shortcut `F4`

Type `C-x, e` to fire off your macro to insert the `(stop)` function in the repl window

# Doing something more musical

{% img img-topic http://2.bp.blogspot.com/-VkwWleTTwuI/TzfwcibV8QI/AAAAAAAAEeY/uwjAdgtY3dw/s1600/novation-launchpad-music-control-surface_1.jpg %} 

Many cool things were done at the hack day and it was great fun to play with the [Ableon Novation Lauchpad](http://www.novationmusic.com/products/midi_controllers/launchpad).  Its a midi controller that can be used to help you play your instruments and make it easier to turn overtone into a song maker.

I got as far as creating a few basic instruments and borrowing a few others, such as the one to create [Jingle Bells](https://gist.github.com/1467798)!

{% gist 1467798 %}

Thanks to [Phil Potter](https://github.com/philandstuff) for having the energy to organise this event, Thoughtworks for supporting us with the venue and everyone there for making it a great day.

To have a whole day focused on overtone really helped me accomplish something and its going to be easier now to keep the learning going.  All my experiments are now uploaded to my github account.

Hope you find the time to make music with Clojure and [Overtone](http://overtone.github.com/), you will love it.

Thank you.
[@jr0cket](https://twitter.com/jr0cket)

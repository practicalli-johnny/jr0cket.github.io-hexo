title: Clojure poetry in motion - developers get creative again at London coding dojo
date: 2012-09-03 05:58:00
categories: coding
tags: 
- clojure
---
{% img img-thumbnail http://3.bp.blogspot.com/-2eAwzw2-ujM/T4q6G9NelbI/AAAAAAAAHQk/wecy_sHn7K8/s1600/ldncljdojo.jpg %} 

The August 2012 coding dojo for the [London Clojure community](http://londonclojurians.org/) brought some creativity to bear, in terms of Clojure, artistic sentiment and a little bare face cheek.

After the usual round of votes for the evenings challenge - which included grand ideas such as re-implementing Emacs in Clojure! - we settled on a poem generator.  Here is what we got up to.

<!-- more -->

Team 4 ([James](https://github.com/weavejester), [Markus](https://github.com/markuskobler), Daniel and myself) used a massively parallel algorithm with a diverse biological origin for the basis of our Haiku poetry generator.  In other words we used the crowd sourcing of Twitter to source all our Haiku poems.

This was not quite the easy and blatant cheat you may think.  As these Haiku poemes were crowd sourced, then we had to develop our own flitering sytem to get rid of retweets, mentions and lots other stuff in each tweet.  Should we decide to go for funding, the filtering will be a big part of our Intellectual Property!

# Anatomy of our solution

{% img img-code http://3.bp.blogspot.com/-oG4of753dRs/UFVh0TBZkGI/AAAAAAAAIWA/dXuANaoqakE/s1600/clojure-dojo-poetry.png %} 

To connect to the Internet we used the really nice [clj-http](https://clojars.org/clj-http) project.  There are some twitter specific projects on Github, but we wanted to go for the simplest approach.  Results were obtained from twitter by specifying a _twitter-url_ and using [clj-http](https://clojars.org/clj-http) to pull back the results and automatically convert them to a json  format.  In fact you get back a persistent map of json results.

Using the magic of the `:keyword` syntax we just pulled out the information we needed from the json results, specifically the `:text` keyword.  As it was sourced from twitter, there was a lot of additional information with each tweet such as name, time of tweet, etc which we wanted to strip out.

As each haiku is supposed to be three lines, we used the clojure function `split-lines` to break up the haiku and check the line count equalled 3.

Once we have some haikus that are the right form, we tidied them up using the handy `coljure.string.replace` function.  We could have done some regex, but again in terms of simplicity then the replace function worked for us.

## Adding some graphics

To add a bit more excitement to our poem  output we decided to put a box around the text.  This was much easier when we used the `pad` function from `clojure.string`.

{% img img-code http://2.bp.blogspot.com/-LHdZ4nUosw4/UFVh-ZipsRI/AAAAAAAAIWI/2_QxwDEVEJ8/s1600/clojure-dojo-poetry-poem.png %} 

Reusing an ansii colour map from `clj-logging`, we quickly added a bit of colour to our box, making it a lovely green colour.

We also considered [quil](https://github.com/quil/quil) (a clojure library for graphics [processing](http://processing.org/)) and [clanci](https://github.com/jr0cket/clansi) (ansi colour and style codes), but as we only had about 30 seconds left using the colour map was the only option we could finish in time.

# Readable code using Threading (-> ->>)

We decided to use the threading operator in some of our functions to help us keep the code readable.  Using `->` and `->>` helps us chain functions together in a particular order.  

Using `->` threading macro the resulting value from the evaluation of one function is passed as the first argument to the next function in the list.  This is the same as the `doto` function (often used to chain events, objects and swing components together). 

Using the `->>` threading macro, the resulting value from the evaluation of one function is passed as the last argument to the next function in the list.

# Using swarm coding is fun and effective

Swarm coding is where you all code on your own machines, but are actually sharing the same session, in this case Emacs running in the terminal window.  James had an environment ready so we all connected to his machine over secure shell (SSH).  Everyone set an environment variable once connected and then James created the clojure project and opened it with Emacs using the no window option which runs emacs in the console window.

    lein new poetry          ; Create a new clojure project
    cd poetry                
    git init                 ; Set up version control with git
    emacs -nw project.clj    ; Run emacs in the terminal window

As we all had the code on our screens we didnt have to squeeze together to see the screen.  With more room its easier to show the REPL and more of the code .  As we all have control over the cursor, we could jump in at any time when we have something to contribute.

I like this approach and can see it working well for a team that communicates well.

# In Summary

The Clojure dojo still remains one of the best ways to really learn clojure and become more confident when writing applications.  I like the use of the `->` and `->>` threading operators to help readability, but do wonder if they detract from the functional style.  I guess some more coding will help me decide.

> Update: after doing more clojure coding, I feel that the threading operator is a really great way to keep your code readable.  If you have several nested functions, then code can take longer to read and comprehend.  Using the threading operator then code is very quickly understood.

> As you are not changing the design of the code then I dont see the threading macro as detracting from the functional style of Clojure.

Thank you.
[@jr0cket](https://twitter.com/jr0cket)

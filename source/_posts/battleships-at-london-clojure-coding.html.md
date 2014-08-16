title: Battleships at London Clojure coding dojo - January 2012
date: 2012-02-07 16:15:00
categories: events
tags: 
- clojure
---

{% img img-thumbnail http://3.bp.blogspot.com/-dHDGQemeztI/TzFK4RV4_zI/AAAAAAAAEbM/AQn4UlfVuWQ/s1600/220px-Battleship_game_board.svg.png %}

Its not quite [Global Thermo Nuclear War](http://en.wikipedia.org/wiki/WarGames), but battleships was a great choice for a coding dojo topic.  Its a simple enough game and therefore a challenge that you feel you can tackle within one evening.  Its also a game that most people know and have fond memories, so the discussions have lots of context.

If you are not familiar with the Battleships game, please see the [Wikipedia page on Battleships](http://en.wikipedia.org/wiki/Battleships_%28game%29). 

At the January 2012 dojo we used a [battleships server created by Neill Alexander](https://github.com/NeillAlexander/battleships) and Robert Rees kindly facilitated the night. The battleships server allows you to submit your "player" and proceeds to play battleship games against is own player - CPU1 (shame the player is not called Master Control Program so I could slip in a Tron reference).

{% img img-topic http://1.bp.blogspot.com/-qlVcL6zWbjY/TzFMw8PPiGI/AAAAAAAAEbs/-Ozv0X_6mrQ/s1600/github-logo.png %} 

To get started with the dojo I forked the project on Github to my own account and cloned the project repository to my local machine.  I still use the command line to clone remote repositories, its pretty straight forward:

    git clone url local-folder-name

For my fork of the battleships game the command becomes

    git clone https://github.com/jr0cket/battleships

> When I clone a github repository that I have forked from someone elses repository I prefix the local folder name with my username so I know its my fork and not the original - saves a lot of hassle wondering why I cant push changes back to github directly

{% img img-topic http://1.bp.blogspot.com/-rxD8__T6tzA/TzFNNTKKLwI/AAAAAAAAEb8/k10iLxa3I70/s1600/leiningen-face.jpg %} 

The project is on my local computer I can fire up leiningen build tool and get the project running.  First thing to do is to make sure I have all the libraries the project depends upon.  Leiningen will download the Internet of jars for me (just like maven) with the following command:

    lein deps

The battleships project uses Clojail to create a sandbox, so its important to set the Java runtime environment security permissions.  There is a handy lein task for this courtesy of Robert Rees that creats a `.java-policy` document in the ... file:

    lein policy

Or you can just create the file with any handy text editor.

{% img img-topic http://1.bp.blogspot.com/-PLeobToC6lc/TzFJCfBSLPI/AAAAAAAAEbE/zSx1cOgHzZE/s1600/emacs128x128icon.png %} 

I then fire up Emacs from within the top level project directory (makes it quicker to find my project files) and opened emacs with the `project.clj` file to see how the project is set up. 

    emacs project.clj &

Clojure has a repl for working with the language dynamically, so I fire the REPL server up using emacs (of course).  Adding **clojure-mode** to emacs 24 gives you the swank REPL server - allowing you to call `clojure-jack-in` and fire up a swank REPl server using the lein project.clj project definition.  I defined a keyboard shortcut `Ctrl-c, Ctrl-j` for the `M-x clojure-jack-in` command in the `.emacs.d/config.el` emacs configuration file.

I then open the relevant clojure code using the keyboard shortcut `Ctrl-c Ctrl-f`.  For the dojo I just needed to work with the `demo.clj` file that defines a battleship player: `jr0cket-battleships/src/battleships/demo.clj`

Once the project is loaded into emacs and swank is running, load the battleships namespace into the swank server using the `(use ...)` function.

Note that `(use)` will load in all the required dependencies at once whereas `(requires)` will also require you add all the dependencies yourself.

    user+> (use :reload-all '[battleships.client :as client])
    nil

For the dojo we had a central server that we all submitted to.  I also spun up a local battleships server so I could do some testing.

    lein ring server

Now I am in the namespace I can submit the player I created - initially this was just the default demo.clj player as I was interested in a baseline player to work with.  By default the demo.clj player will shoot and place your ships at random, with no intelligence to these
actions

    user> (submit-player "src/battleships/demo.clj" "baseline" "http://localhost:3000")
    Submitting to http://localhost:3000/create
        {:status 200, :headers {"date" "Tue, 31 Jan 2012 21:24:18 GMT", "content-type" "text/html; charset=utf-8", "connection" "close", "server" "Jetty(6.1.25)"}, :body "player1912"}

When submitting your "enhanced" player you should give it a name you will remember, different from other players.  As the game does not replay any matches, its probably worth submitting a new player rather than updating an existing one (there would have to be a lot of players to overload the server!).

    user> **(submit-player "src/battleships/demo.clj" "Masher001" "http://localhost:3000")**
    Submitting to http://localhost:3000/create
    {:status 200, :headers {"date" "Tue, 31 Jan 2012 21:24:18 GMT",
    "content-type" "text/html; charset=utf-8", "connection" "close",
    "server" "Jetty(6.1.25)"}, :body "player1912"}

If you are playing against each other in teams, then the server address will be the  IP address of a shared server.

{% img img-thumbnail http://3.bp.blogspot.com/-te_MuKdFBTQ/TzFLahe2BxI/AAAAAAAAEbY/Bn_JPN_s3qU/s1600/clojure-logo-500x.png %} 

Now the clojure fun begins.  Using the demo.clj as a basis, modify your player so it wins all the games, or at least stop it from sucking more than everyone else’s player.

So if you want to have some Clojure fun with Battleships, go make your own fork of the [Battleships server](https://github.com/NeillAlexander/battleships) and get coding!

Thank you.
[@jr0cket](https://twitter.com/jr0cket)

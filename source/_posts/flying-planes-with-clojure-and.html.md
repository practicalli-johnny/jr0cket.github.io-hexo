title: Flying planes with Clojure and FlightGear
date: 2013-03-21 21:33:00
categories: clojure
tags: 
- clojure
- coding
- events

---

Dale Thatcher from the [London Clojure community](http://londonclojurians.org/) created a [Clojure project](https://github.com/dalethatcher/flightgear) that allows you to fly a plane in real time.  Now, Dale has not yet connected this to a real plane, instead he is using the open source flight simulator, [FlightGear](http://www.flightgear.org/).

I took Dale's project for a test flight and here are my experiences!

<!-- more -->

# Getting set up

I am using Ubuntu 12.10 and FlightGear is in the software center, so its easy to add it.  Be aware that the file is 635MB in size (1.3GB once installed), so you need a decent Internet connection and a fair bit of space.

You can of course use `apt-get` on the command line too:

    sudo apt-get install flightgear

{% img img-code http://3.bp.blogspot.com/-xbgiADIrEtI/UUtjzKwkFwI/AAAAAAAAJLk/3CWfbfuBtRQ/s1600/flight-gear-ubuntu-software-center.png %}

# Running FlightGear

{% img img-topic http://1.bp.blogspot.com/-9ILGm7ZzlQg/UUtrWInCpRI/AAAAAAAAJL0/AAnahKbG9jg/s1600/flight-gear-telnet-port.png %}

Whilst there are GUI tools to run FlightGear, I just went for the command line.  Following Dale's guide, I ran the emulator with a specific Telnet port.  I am assuming this is what the library uses to communicate with.

Now you should see a plane cockpit, ready and waiting for you to jump into the controls.

{% img img-code http://4.bp.blogspot.com/-7N9oGY9vJxw/UUtscbmeA7I/AAAAAAAAJL8/cwUFirHQW4A/s1600/flight-gear-cockpit.png %}

# Setting up the Clojure project

I created a basic Clojure project using Leingen, of course.

    lein new my-flight

Editing the `my-flight/project.clj` project file, I added a dependency on Dale's flightgear project

{% codeblock lang:clojure project.clj %}
:dependencies [[org.clojars.dalethatcher/flightgear "0.1.0-SNAPSHOT"]]
{% endcodeblock %}

The project file should look like this: 

{% img img-code http://3.bp.blogspot.com/-M1XTODPYNx0/UUts21J6I7I/AAAAAAAAJME/Pp81KaVtJMM/s1600/my-flight-project.clj.png %} 

> You may have a newer version of Clojure than in the above example.

I could write a few Clojure functions to control the airplane, but I dont know how responsive it will be.  So instead I fired up the REPL, connected to the flight simulator over the telnet port and started issuing command.

Much more fun and much faster feedback.


{% codeblock lang:clojure Clojure REPL %}
(use 'flightgear.api)
(connect "localhost" 5401)
(starter! true) ; wait until engine started
(starter! false)
(flaps! 0.5)
(throttle! 1)  ; wait for a little while and you should be airbourne
(rudder! 0.1) ; steer a bit to the right (single props tend to veer to one side)
{% endcodeblock %}

It works.  I am controlling the plane and am trundling off down the runway.

I am assuming this control interface mimics what you have to do in the simulator, as otherwise I'd have prefered the starter motor to turn itself off.  I know very little about flying planes.

# Learning to fly

All this has been fairly easy so far.  Well easy compared to actually being able to fly the plane without crashing after 30 seconds.

Using the Clojure REPL I can issue commands to tweak the flight of the plane, adusting thrust, flaps, etc.  As its a single propeller plane, it tends to vere about a bit, so needs constant input to keep it flying. 

I think the best chance of flying this plane is to write a Clojure program to do it for me.  Luckily, Dale's project included Telemetry information such as position, velocity and orientation.

Its going to be great fun learning to fly and I havent even looked at the game options such as weather (I may turn all that off at first!).

The FlightGear game and Dale's Clojure project should give me hours of fun (assuming I can find the time).

Thank you.
[@jr0cket](https://twitter.com/jr0cket)

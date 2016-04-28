title: Beginners guide to HTML5 Apps
categories: events
tags:
---

Nick Brown - London HTML5 meetup

The HTML5 User Group returns to Skills Matter for a Beginners Guide to creating HTML5 apps utilising HTML5 on the client side and Nodejs for the server.

HTML5 user group lead and CEO of [Boss Level](http://www.bosslevelgames.com/), Nick Brown:

A lot of people were interested in Node and whilst technically Node isn't part of the [HTML5 specification](http://www.w3.org/html/wg/drafts/html/master/), it is increasingly being used by "all the trendy kids" ;-) It does also utilise Javascript which is obviously the primary language for this sort of thing. So what I'll do is show some basic client/server communication and essentially how we do things at Boss Level and make the whole thing a Q&A session with code examples.


http://en.wikipedia.org/wiki/HTML5

http://playscavengers.com/

Nicks requirements

- single page app with communication handled by WebSockets
- unified UI design and navigation across platforms (desktop,mobiles, tables)
- gaming so graiical ly intense with low bordem threshold  -- 8 canvas elements stacked on top of each other, sprites bulit on the fly
- no SEO, content or accessibility - no symantic website
- freemium model - in app payments
- anything other than the latest browsers are not supported - no feasable alternative if a browser does not support HTML5 canvas.
- heavy performance baised app with potential speed and membory botlenecks.  Other apps build have other primary issues, such as load times.


# Terminology checklist

## Events / Event loops
Event driven programming on both the client and server side.  You bind click events, etc and most of the code is triggered by events.  Nodejs is cool, but traditional webservers scale up by getting bigger and bigger boxes (RAM, CPU).  Nodejs has a single connection only.  It talkes a request and and processes, then does the next one.  No one can connect until you have finished dealing with your request.

You must not block the event loop.

## WebSockets
A lightweight protocol, the smallest thing you can send can be as small as two bytes.  TCP is very heavyweight in comparison.


## Caching
Is very important both on the client and server side.  Nodejs doesnt enable caching in development model


## Proxying and load balancing
To scale your architecture, you put a load balancer across multiple servers and manages the load across all your servers.

Proxying is where you take a port and map it across to a different one.

Nodejs is based on the unix model, specific tasks doing one thing really well.  Nick has lots of different servers that run different tasks, all running on different ports.  Proxying will map ports that are not typically accessable over the web from ports that are (80, 433).


## Modular code

Although they server up just one file, the app is composed of many many files. Nick uses *require* to assemble all the files into one.  (Google)


## Asynchronous

Call backs.  Functoin b is called from function A and as it has a call back, it has a way to get back to the calling function A.

In Javascript you just have function scope.  Either global or local to functions.

Javascript the Good Bits - Douglas Crockford.


## HTML5 api's
- local storage,

- web workers -- offloading processing.  There is an overhead, so it needs to be worth while, process lots of stuff.  It is just Javascript processing and so therefore there is no dom access and thererfore cant be used for canvas.

- offline apps - can use local storage so you dont have to have an internet connection.  Beware about putting IP code locally as people can look at it with a view source.

- Media Queries -- applying css styles base on the device profile.  Not flexible enough for Nicks requirements, he wanted pixel perfect rendering.


## JSON - Doug Crockford


## Responsive web design

## TDD
Its what we should be doing, but we don't as we are a startup.



# Typical Architecture

A client

A server + load balancing, static asset serving, firewall, portforwarding, NodeJS, PHP, Rails

A database - MongoDB (player details, teams, etc.), Redis (handles most of that stuff in memory, so handling session state)

Nodejs is used for caching


# Tools

## IDE

## Debuggers (Mark uses Chrome, better debugger tooling)
- firebug, webkit web inspector, v8-profiler, Node Inspector, Console.log('status',player.status)
-- google for videos on debugging

## Versioning

## Build script
- deploys using bash scripts

## Web Sites
- CSS generators, Modernizr

# The client

## CSS
html, CSS (.classes, #ids and key-frames) -- quickets way to get something in a dom is to give it a unique id and append it to the document as we generate it on the fly.
-- classes are important to manage css animiations easily, enabling you to move graphics by changing it classes
-- key-frames - ofloading your animiations.  It works much smoother than the janimate function that dies if too much stuff is going on.

## frameworks
jQuery is used but it can be a bit big and bulky.  Its still used as its quite embedded in the code, but it will be pulled out.  It does handle lots of cross browser stuff though.

## managing styles cross browser
Mondernizer or Normalise makes sure you are using the right styles across browsers.

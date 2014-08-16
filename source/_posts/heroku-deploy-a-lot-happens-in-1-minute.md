---
layout: post
title: "Heroku deploy - a lot happens in 1 minute"
date: 2014-03-26 19:36:33 +0000
comments: true
categories: cloud
tags: heroku
---

As technology progresses then taking a few minutes to deploy your app can seem like a long time, but when you consider everything Heroku is doing during that time then its quite amazing

<!-- more -->

## Provision server resources & managing traffic
Heroku creates a new "server" each time you deploy, so that the currently live application can still handle reuests until the new version is ready.  Rather than a whole bloated server, Heroku actually creates a new Linux container with a running OS.  This Linux container usually takes a second or less to create with a running operating system.

## The environment is then established
Every language you use to write your application needs some kind of runtime, eg. if you need Java you need the JVM, Ruby apps need a particular version of Ruby, Javascript probably needs nodejs and PHP needs a webserver.  As part of the Heroku buildpack used during the deployment, the relevant libraries and platforms are brought in.  Unless you change the configuration of your build or the buildfile you use, Heroku will always bring in the same version of the environment you need to run your app each time you deploy.

## Compilation of code
If your app is compiled, then the build process is run so you have a deployment made from your standard production build.

Environment variables are set for the applications and any services (caching, logging, monitoring, etc) or datastores (postgres, redis, mongodb) are therefore automatically connected too.

All the relevant processes are run and scalled (can you scale your app to a certain level when you deploy)



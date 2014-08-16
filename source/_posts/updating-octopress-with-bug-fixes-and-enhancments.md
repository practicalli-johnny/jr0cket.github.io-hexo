---
layout: post
title: "Updating Octopress with bug fixes and enhancments"
date: 2014-03-13 19:32:54 +0000
comments: true
categories: blogging
tags: octopress
---

For each Octopress project you have created (ie. for each blog / website you created with Octopress) you need to pull some code from Github remote (octopress master) and run a few rake tasks.

Before you start with an update, check you Octopress projects files have been added to the Git repository or Stashed out of the way - as Octopress will try and overwrite them (although as its using git it will fail and warn you about a merge conflict).

    git pull octopress master     # Get the latest Octopress
    bundle install                # Keep gems updated
    rake update_source            # update the template's source
    rake update_style             # update the template's style

http://octopress.org/docs/updating/

Thank you
[@jr0cket](https://twitter.com/jr0cket)

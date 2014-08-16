---
layout: post
title: "First blog post ever - awesome"
date: 2014-03-03 00:08:42 +0000
comments: true
categories: blogging
tags:
- octopress
---

This is the first blog post of many in my adventures in learning how to publish a blog using Octopress.  

As a developer I want a lightweight tool to create and easily publish content interesting to other developers in the community.  Although I can write HTML, CSS and JavaScript for webapps, I dont want to be slowed down writing these things when I am doing creative writing.

Using Octopress, which is a blogging framework on top of Jekyll, I can write my content using Markdown.  As Markdown is just simple text with a few characters and indents used for formating, I can focus on the writing and make it as appealing as I can.  I dont get distracted by the visual layout of the content and a standard design for the blog is consistently applied.
<!-- more -->

The only challenge I had intially was to get a working copy of Ruby running on my Ubuntu laptop.  Jekyll and therefore Octopress requires Ruby version 1.9.3 or greater and Unfortunately I seemed to have a mix of 1.9.1 and 1.9.3.  In Ubuntu 13.10 there is a strange stiuation where the 1.9.3 version of ruby was installed along side version 1.9.1 and therefore errors arrose when trying to generate the site.

To fix Ruby on Ubuntu, I loaded up Synaptic package manager and removed all Ruby packages and anything related, such as gem and bundler.  Then I installed the package ruby2.0 along with the docs and dev packages for that version.  With only the latest version of Ruby installed, Octopress worked perfectly.

I look forward to sharing my further experiences blogging with Octopress

Thank you.
[@jr0cket](https://twitter.com/jr0cket)




---
layout: post
title: "Creating blog posts with Octopress"
date: 2014-03-04 15:46:14 +0000
comments: true
categories: blogging
tags: octopress 
---

Octopress provides an easy way to create blog posts by proving a task that will automatically place and name your markdown file.  This helps manage your blog posts in a sensible structure and avoids conflicts.

To create a new post, use the following command inside your Octopress project folder:

{% codeblock %}
rake new_post["Title of your blog post"]
{% endcodeblock %}

This will create a markdown file including frontmatter to apply the blog post style.  The task creates the file under the _source folder and included the date at the start of the filename.

<!-- more -->
Now you can edit the file and simply add your content.  Once you have written your blog post you can ask Octopress to generate the html for your new post.

{% codeblock %}
rake generate 
{% endcodeblock %}

You can view the results locally, or simply deploy up to your chosen location (eg. github pages)

{% codeblock %}
rake preview
rake deploy  
{% endcodeblock %}

If you are confident about the changes you are making, or have a test website you are deploying to, then you can use a single command to generate the new version of the site and publish it directly.

{% codeblock %}
rake gen_deploy
{% endcodeblock %}


## Summary 
This covers the bloggine workflow for Octopress.  Next we will cover adding content in your blog post markdown files, inlcuding text formatting, images, code snippets, embedded video, etc


Thank you

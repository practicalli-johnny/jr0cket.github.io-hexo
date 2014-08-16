title: Creating your first post with Hexo.io
date: 2014-03-27 01:36:58
tags: hexo
---

{% img img-thumbnail /images/hexo-logo.png %}

So you have installed Hexo (and nodejs), so now you are ready to start blogging.  Use the following command to create a new blog post entry (blog posts are the default type of content, although this can be changed in _config.yml):

    hexo new "Meaningful blog post title with a hint of SEO"

Hexo will create a new file under source/_posts using the name provided.  You can then edit this file and start creating your content using Markdown.

<!-- more -->

# Generating and viewing your blog

When you have finished writing your content, you can generate your blog posts using the command:

    hexo generate 

This will convert your markdown content into a static website.  Then you can view the site by running it on a server that Hexo provides:

    hexo server 
 
If everything looks good then you may want to publish the generated website somewhere it can be more readily accessed via the Internet.  Once such place is Github Pages (cover this later).

Later on you may want to tweak your theme and general configurations for the website.

# Tweaking the Hexo site configurations

Just like with Octopress, you edit the _config.yml file and add your name, URL and any other details and settings you want to apply to the general blog.


# Quick summary: Seting up Hexo

In case you forgot how to set Hexo up, then it is basically:

* Download the nodejs binaries (or compile from source if you have time to kill)
* Add nodejs to the path (a setting in your shell rc file - eg. ~/.bashrc or ~/.zshrc)
* Install hexo using: npm install hexo -g (wait for npm to download all the node packages)
* Create a new website using: hexo init website-name (where website-name is just the folder name for your website project)

Thank you
[@jr0cket](https://twitter.com/jr0cket)

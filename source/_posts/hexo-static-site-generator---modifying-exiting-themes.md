title: Hexo Static site generator - modifying existing themes
date: 2014-04-02 07:45:21
categories: blogging 
tags: 
- hexo
---

{% img img-thumbnail /images/hexo-logo.png %}
Hexo is a great way to create a blog or static website and comes with some responsive and great looking themes.  However, so your site doesnt look like everyone elses, you may want to customise the look and the easiest way is to modify an existing theme.

<!-- more -->

## Landscape - the default theme

There are a wide range of themes to choose from, althought Landscape is one of the newest and is also the default so you dont need to instal it.

### Location of themes 

In the themes folder of your hexo project 

    hexo init new-project
    cd new-project

You will now see a `themes/landscape` directory structure in your new hexo project.  Inside this landscape directory are a collection of files that generate the theme when you run ethier `hexo server` or `hexo generate`.

 


## Making your changes work

If you have already generated or deployed your site with a theme and then you modify it. it seems hexo does not pick up those changes.  First you need to run the command

    hexo clean 

This will remove the cache and the .deploy folders.  So now when you do

    hexo generate

all new files are added to public.

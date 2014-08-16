---
layout: post
title: "Create great looking website content with Twitter Bootstrap"
date: 2014-03-08 08:16:30 +0000
comments: true
catagories: blogging
tags: 
- bootstrap  
---


## What is Twitter bootstrap?

Bootstrap is an HTML5 toolkit from Twitter to help kickstart webapps and web content sites.  It includes a base Cascading Style Sheet (CSS) and HTML for forms, buttons, typography, tables, grids, navigation and much more.

Bootstrap stylesheet provides an easy-to-implement 960 grid for efficient layout, as well as expertly crafted styles for typography, navigation, tables, forms, buttons, and more. To take care of everyday JavaScript touches, Bootstrap provides a well built set of jQuery plugins for drop-down menus, tabs, modal boxes, tooltips, alert messages, and more.

This helps you create a standards compliant, responsive, user-friendly, professionally built HTML5 website, right out of the box. 

<!-- more -->

## Licencing

Bootstrap is under the Apache 2.0 license, provide a great deal of creative freedom. So long as you give the good folks at Twitter due credit for their work, you're free to take, tweak, and customize everything to your heart's content.

## Getting started with Bootstrap

If you just want to use Bootstrap for your project you can simply include the minified libraries from a content delivery network 

{% codeblock lang:html Use Bootstrap from a Content Delivery Network (CDN) %} 
<!DOCTYPE html>
 <html>
 <head>
   <meta charset="utf-8">
   <meta name="viewport" content="width=device-width, initial-scale=1">
   <title>Hack the Tower - London hackday</title>
   <link href="http://netdna.bootstrapcdn.com/bootstrap/3.1.1/css/bootstrap.min.css" rel="stylesheet">     
   <link href="http://netdna.bootstrapcdn.com/bootswatch/3.1.1/united/bootstrap.min.css" rel="stylesheet">
   <link href="css/hackthetower.css" rel="stylesheet">
 </head>
{% endcodeblock %}

In the example, lines 8 & 9 include minified bootstrap using the **netdna** content delivery network (CDN), so where ever people view your site from around the world it should not slow down due to loading these styleheets.

You can now use elements from Bootstrap in your project and view the results anywhere you have an internet connection.  To learn what these are, take a look at [Get Bootstrap](http://getbootstrap.com/) or Google for some of the very many examples out there.

## Working with Bootstrap

If you want to see the styles that bootstrap uses or carry out some significant customisations, you can also download bootstrap to your laptop as normal CSS files.  Its common practice to put cascading stylesheets into a folder called CSS and JavaScript in a folder called javascript.

If you are doing significant customisation then you could edit the twitter bootstrap files directly.  Alternativley you can create your own CSS and JavaScript files that over-ride the bootstrap styles and scripts.

## Resources

The following links will give you ideas on how to make the most out of Bootstrap:
- [Get Bootstrap - Getting Started](http://getbootstrap.com/getting-started/)
- Tutorial: [Up and running with Twitter Bootstrap in 20 minutes](http://www.revillweb.com/tutorials/twitter-bootstrap-tutorial/)
- Tutorial: [w3resource: Twitter Bootstrap 3 tutorial](http://www.w3resource.com/twitter-bootstrap/tutorial.php)
- Video: [Bootstrap Tutorial For Beginners - Responsive Design with Bootstrap](https://www.youtube.com/watch?v=no-Ntkc836w)
- [Official Bootstrap blog](http://blog.getbootstrap.com/)
- [StackOverflow - Twitter-Bootstrap-3](http://stackoverflow.com/questions/tagged/twitter-bootstrap-3)
- [@twbootstrap](https://twitter.com/twbootstrap)

Thank you.
[@jr0cket](https://twitter.com/jr0cket)

title: Hexo theme - using Ubuntu Google fonts
date: 2014-06-16 23:37:17
categories: blogging
tags:
- hexo
---

{% img img-thumbnail /images/hexo-logo.png %}

The font that comes with the default hexo fault is quite nice, however, I like using the Ubuntu font especially for code.  As the Hexo theme uses Google fonts in some places already, then it was really easy to change which one Hexo uses.  Here I will show you how to change over to the Ubuntu font family for text and sorce code using [Google Fonts](http://www.google.com/fonts).

<!--  more -->

# Defining fonts in Hexo

As Hexo uses Google Fonts by default, then you can simply define which font you want by using the font name.  The default Heox theme, landscape, uses a file called `source/css/_variables.styl` to define common variables, such as fonts.  

Viewing the `_variables.styl` file you can see the fonts that Hexo uses by default, which are assigned to three variables:

* font-sans
* font-serif
* font-mono - (source code) 
* font-icon - (icons in navbar) 

>Font-icon is configured to use Font Awesome to make it quick and simple to add logos such as twitter, facebook, linkedIn and RSS feeds.  Using font icons is more efficient than using image files as they are scalable, so no need for multiple image files for the logos.

``` source/css/_variables.styl
// Fonts
font-sans = "Helvetica Neue", Helvetica, Arial, sans-serif
font-serif = Georgia, "Times New Roman", serif
font-mono = "Source Code Pro", Consolas, Monaco, Menlo, Consolas, monospace
font-icon = FontAwesome
font-icon-path = "fonts/fontawesome-webfont"
font-icon-version = "4.0.3"
font-size = 14px
line-height = 1.6em
line-height-title = 1.1em
```

This is what the fonts in the hexo default theme look like: 

{% img img-code /images/hexo-theme-original-fonts.png %} 

# Updating Hexo to use the Ubuntu fonts 

I prefer to use the Ubunt fonts, for text and for source code.  So I updated the `source/css/_variables.styl` file with Ubuntu for the font-sans and font-serif variables and Ubuntu Mono for the font-mono variable.

``` source/css/_variables.styl
// Fonts
font-sans = Ubuntu, sans-serif
font-serif = Ubuntu, serif
font-mono = "Ubuntu Mono", monospace
font-icon = FontAwesome
font-icon-path = "fonts/fontawesome-webfont"
font-icon-version = "4.0.3"
font-size = 14px
line-height = 1.6em
line-height-title = 1.1em
```

Using Ubuntu fonts just works on my laptop, as I use Ubuntu as my operating system and the Ubuntu fonts are just there.  When I publish my Hexo website, I cant guarantee everyone is using Ubuntu so I use Google Fonts to spread the Ubuntu font love.

# Google Fonts 

Google fonts are a wide range of open fonts hosted in the cloud and part of a content delivery network (CDN).  This means that a whole range of fonts are freely availble to be used in your own websites and apps.  The content delivery network ensures these fonts are loaded (relatively) quickly anywhere in the world. 

You can browse the fonts avaible for use and see the code to include them in your websites by visiting [google.com/fonts](http://www.google.com/fonts)

To keep these fonts as lightweight as possible whilst loading into the browser, I chose only the Ubuntu fonts I needed.  In this case, I chose the Ubuntu Normal and Italic fonts at 400 weight and bold at 700 weight 

``` html 
<link href="http://fonts.googleapis.com/css?family=Ubuntu:400,700,400italic" rel="stylesheet" type="text/css">
```

I also want to show code in the Ubuntu Mono typeface at both 400 and 700 weight for normal and bold text respectively.  Google Fonts website generates me the following link I can use in my Hexo website.

``` html 
<link href="http://fonts.googleapis.com/css?family=Ubuntu+Mono:400,700|Ubuntu:400,700,400italic" rel="stylesheet" type="text/css">
```

# Adding the Ubuntu Google Fonts to Hexo

I updated my custom theme to use the Ubuntu Google fonts by editing the `layout/_partial/head.ejs` file.  This already had a Google Font for Source Code Pro, so I simply replaced that line with the new URL I got from Google Fonts as above.

``` html layout/_partial/head.ejs
  <title><% if (title){ %><%= title %> | <% } %><%= config.title %></title>
  <meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1">
  <%- open_graph({twitter_id: theme.twitter, google_plus: theme.google_plus, fb_admins: theme.fb_admins, fb_app_id: theme.fb_app_id}) %>
  <% if (theme.rss){ %>
    <link rel="alternative" href="<%- theme.rss %>" title="<%= config.title %>" type="application/atom+xml">
  <% } %>
  <% if (theme.favicon){ %>
    <link rel="icon" href="<%- theme.favicon %>">
  <% } %>
    <link href="http://fonts.googleapis.com/css?family=Ubuntu+Mono:400,700|Ubuntu:400,700,400italic" rel="stylesheet" type="text/css">
  <%- css('css/style') %>
  <%- partial('google-analytics') %>
</head>
```

> Line 10: Ubuntu fonts included from Google Fonts

When Hexo generates all the theme files, the Google Docs URL for the Ubuntu fonts gets included in the head part of all pages.  This ensures that even thought without Ubuntu fonts installed on their device will see the page with Ubuntu fonts.


# Testing the font change

Changes to the `source/css/_variables.styl` file are picked up straight away if you are running the command `hexo server`, so all you would need to do is refresh your browser.


Hexo with the Ubuntu fonts looks like:

{% img img-code /images/hexo-theme-ubuntu-fonts.png %}

# In Summary

Changing to Ubuntu fonts or any other Google font is pretty easy with Hexo.  It may not seem a big change that I have made, but as I refer to my blog many times during the week (and sometime many times a day), its nice to have a font that I find pleasing to read.

Thank you.
[@jr0cket](https://twitter.com/jr0cket)

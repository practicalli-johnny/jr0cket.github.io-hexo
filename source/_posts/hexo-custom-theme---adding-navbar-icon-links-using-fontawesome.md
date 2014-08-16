title: Hexo custom theme - using FontAwesome icons
date: 2014-06-01 19:50:09
categories: blogging
tags: 
- hexo 
---
{% img img-thumbnail /images/hexo-logo.png %}

[FontAwesome](http://fortawesome.github.io/Font-Awesome/) provides a lot of icons you can use in your website instead of including image logos of various sizes.  There are icons for twitter, linkedin, Github and RSS feeds.  Using these icons keeps your website fast on any device or network.

I'll explain how I configured the standard [Hexo Landscape theme](https://github.com/hexojs/hexo-theme-landscape) to add icons in my blog website navigation bar, each icon linking to the developer related sites I use such as Github and Twitter.

<!-- more --> 

# FontAwesome icons are awesome

FontAwesome is a font that has a wide range of icons, including logos from common websites such at Twitter, Github, LinkedIn, etc.  Using a font for these logos is more efficient when it comes to load times of your website, as you only need to include one font which scales to different sizes.

{% img img-code /images/font-awesome-icons.png %}

# Adding Icons Styles to the CSS

The Hexo theme already had two CSS ID's defined in the header styles, providing icons for the RSS feed and search button.  I simpy copied these style definitions for the addtional icons I wanted, giving each icon its own unique CSS ID.

To get the correct code for the FontAwesome icon I wanted, I refered to this [list of CSS content values](http://astronautweb.co/snippet/font-awesome/).

I updated the `source/css/_partial/header.styl` file to include the additional icon styles.

{% codeblock source/css/_partial/header.styl lang:css %}
#nav-rss-link
  &:before
    content: "\f09e"

#nav-twitter-link
  &:before
    content: "\f099"

#nav-linkedin-link
  &:before
    content: "\f0e1"

#nav-googleplus-link
  &:before
    content: "\f0d5"

#nav-github-link
  &:before
    content: "\f113"

#nav-search-btn
  &:before
    content: "\f002"

{% endcodeblock %}


# Adding Icons to the header layout

Now the icon style are defined, we need to include them in the navigation bar layout.  This navigation bar layout is defined in the file `layout/_partial/header.ejs`, see lines 3,4,and 5 below: 

{% codeblock layout/_partial/header.styl lang:javascript %}
      <nav id="sub-nav">
        <a id="nav-github-link" class="nav-icon" href="https://github.com/jr0cket" target="_blank"></a>
        <a id="nav-linkedin-link" class="nav-icon" href="https://uk.linkedin.com/in/jr0cket" target="_blank"></a>
        <a id="nav-twitter-link" class="nav-icon" href="https://twitter.com/jr0cket" target="_blank"></a>
        <a id="nav-googleplus-link" class="nav-icon" href="https://plus.google.com/117080433375668558463" target="_blank"></a>
        <% if (theme.rss){ %>
          <a id="nav-rss-link" class="nav-icon" href="<%- theme.rss %>" title="RSS Feed"></a>
        <% } %>
        <a id="nav-search-btn" class="nav-icon" title="Search"></a>
      </nav>
{% endcodeblock %}

# The finished result 

As soon as both files are saved, I can see the results as soon as I refresh the browser as I am running `hexo server`.  

My navigation bar now has more icons displayed, each icon linking to my other developer websites

{% img img-code /images/hexo-theme-navbar-icons-fontawesome.png %}

The navigation bar has a link for my Github, LinkedIn, Twitter and Google plus profile pages.

Thank you
[@jr0cket](https://twitter.com/jr0cket)

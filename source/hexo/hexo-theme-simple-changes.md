title: Customising the Hexo theme
date: 2014-07-02 14:05:00
---

There are some very simple changes you can make to the Hexo Landscape theme without having to dig into the code that makes it work.  You can edit the theme configuration file and make changes to the navigation bar along the top, what sidebar components appear and 


# Adding links to the top navbar

The Hexo theme has two links on the top navbar, _Home_ and _archives_.  By editing the theme configuration file, `themes/landscape/_config.yml`

``` yaml themes/landscape/_config.yml
# Header
menu:
  Home: /
  Archives: /archives
rss: /atom.xml
```

``` yaml themes/landscape/_config.yml
# Header
menu:
  Home: /
  Clojure: /clojure
  Hexo: /hexo
  Ubuntu: http://ubuntu.jr0cket.co.uk
  Archives: /archives
rss: /atom.xml
```
This add 3 more items to the navbar, two are links to pages inside the hexo website and one is a link to an external website I have on Ubuntu.

{% img img-code hexo-theme-simple-changes-top-navbar.png %}


# Changing the sidebar 

The sidebar of the landscape theme is made up of individual parts.  You can select which sidebar parts you want to display and in what order.  Simply edit the theme configuraton file, `themes/landscape/_config.yml`

``` yaml themes/landscape/_config.yml
# Sidebar
sidebar: right
widgets:
- category
- tag
- tagcloud
- archive
- recent_posts
```

# Shrinking spaces between posts & sidebar elements

Reduced the block margin from 50 to 24px

// Layout
// Margin around each content block (ie. space around each blog post box and sidebar box)
block-margin = 24px
article-padding = 20px
mobile-nav-width = 280px
main-column = 9
sidebar-column = 3


# Making the code blocks nicer with curves

The code that defines the code block is generated in the file `themes/landscape/source/css/_partial/highlight.styl`

``` css themes/landscape/source/css/_partial/highlight.styl
$code-block
  background: highlight-background
  margin: 0 article-padding * -1
  padding: 15px article-padding
  border-style: solid
  border-color: color-border
  border-width: 1px 0
  overflow: auto
  color: highlight-foreground
  line-height: font-size * line-height
```

To add curves to the code block corners and put a margin around the code block, the following was added to the end of the above code-block definitions

``` css themes/landscape/source/css/_partial/highlight.styl
  border-radius: code-border-radius
  background: #333;
  margin: 1px 10px 1px 10px
  border: 3px solid #EEEEEE;
```

The `code-border-radius` is defined in the `themes/landscape/source/css/_variables.styl` file



[Back to Hexo overview](index.html) | [Deconstructing the Hexo theme](deconstructing-the-hexo-theme.html)


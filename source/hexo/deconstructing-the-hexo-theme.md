


# Deconstructing the Hexo theme

CSS is generated from definitions written in Stylus, a simpler way to write CSS 

Layouts are defined using a series of files written in E...


# Changing the Banner Images

Existing Banner

``` yaml themes/landscape/css/_variables.styl
// Header
logo-size = 40px
subtitle-size = 16px
banner-height = 300px
banner-url = "images/banner.jpg"
```

My new Banner

``` yaml themes/landscape/css/_variables.styl
// Header
logo-size = 40px
subtitle-size = 16px
banner-height = 120px
banner-url = "images/jr0cket-banner-dual-clojure.png"
```

# Navbar links opacity

Decrease the opacity of the navbar links so they show up more clearly, but still keep the text lightening up when the mouse hovers over them.

[stylesheet opacity setting in css somewhere]


# Changing fonts use for site

Hexo uses google fonts 

``` yaml themes/landscape/css/_variables.styl
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

Being a user of Ubuntu Linux, I really enjoy using the Ubunt family of fonts.  I think its one of the best designed fonts out there in terms of design and readability.

I updated the theme _variables.styl file to use Ubuntu fonts

``` yaml themes/landscape-jr0cket/css/_variables
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


# Shrinking blockquote

I use block qoute in my content to denote something that is extra that is not the main focus o f the article.  I therefore wanted to make it smaller and make it italic

``` css themes/landscape-jr0cket/source/css/_partial/article.styl
  blockquote
    font-family: font-serif
    font-style: italic;
    font-size: 0.96em
    margin: line-height 20px
    text-align: center
```


# Creating Image styles 

There seems to be only one style for images.  I wanted to have three different styles, for article thumbnails (similar to slashdot), side images to highlight different topics or tools covered in an article and larger central images to show code snippets and screenshots.

So I have created three styles:

* img-thumbnail
* img-topic
* img-code 


``` css themes/landscape-jr0cket/source/css/_partial/article.styl
  blockquote
  .img-thumbnail
    max-width: 240px
    max-height: 96px
    display: block
    margin-right: 12px
    margin-top: 12px
    float: left
    clear: left
  .img-code
    max-width: 640px
    max-height: 320px
    display: block 
    margin-left: auto
    margin-right: auto  
  .img-topic
    max-width: 360px
    max-height: 1800px
    display: block 
    margin-left 12px
    margin-right: 12px
    margin-top: 12px
    margin-bottom: 12px
    float: right
    clear: right
```


# Mobile menu

Changing the background colour

``` yaml themes/landscape/css/_variables
color-mobile-nav-background = #191919
```

``` yaml themes/landscape/css/_variables
color-mobile-nav-background = #1f0542
```


# Domain name stuff


UK reg default IP address for A record - jr0cket.co.UK
88.208.252.9


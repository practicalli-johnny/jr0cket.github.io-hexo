title: Hexo custom theme - maximising the layout of the website
date: 2014-06-03 15:52:05
categories: blogging
tags: 
- hexo 
---

{% img img-thumbnail /images/hexo-logo.png %}

Whilst I like many aspects of the Hexo theme used to generate static websites, it does seem to have a lot of redundant space.  So here are a few aspects of the them I have changes in order to get more of the actual content showing on the page.

<!-- more -->

# Scaling down the header space

The most obvious occurance is the header image, which takes up a huge part of the screen on the desktop.


# Scaling down the image


# Changing the image

The most obvious way to make your website look different from all the other Hexo generated websites is to change the header image.

## Header image with my cat
Very personal, not neccessarily representative of the website content though.

Also not that easy to see the text in the top navigation bar, as the text and icons are white and the background image is light.

Boosting the opacity of the naviation text and icons makes them stand out better on the lighter background.

### Chaning Navbar text opacity

The CSS definition called nav-link contains an opacity value.  This was changed from 0.6 (60 percent) to 0.8 (80 percent) to make the navbar links more visible when hovering over them with the mouse.

{% codeblock source/css/_partial/header.styl lang:css %}
$nav-link
  float: left
  color: #fff
  opacity: 0.8
  text-decoration: none
  text-shadow: 0 1px rgba(0, 0, 0, 0.2)
  transition: opacity 0.2s
  display: block
  padding: 20px 15px
  &:hover
    opacity: 1
{% endcodeblock %}


## Increase the size of the logo text

I change my logo to say "community developer" and wanted it to take up less room in the header.  So I found the CSS declaration for `logo-text` and increased the font weight from 300 to 700

{% codeblock source/css/_partial/header.styl lang:css %}
$logo-text
  text-decoration: none
  color: #fff
  font-weight: 300
  text-shadow: 0 1px 4px rgba(0, 0, 0, 0.3)
{% endcodeblock %}  
  
 The same for the main-nav-link text
 
{% codeblock source/css/_partial/header.styl lang:css %}
.main-nav-link
  @extend $nav-link
  font-weight: 700
  letter-spacing: 1px
  @media mq-mobile
    display: none
{% endcodeblock %}


## More navbar changes 

* Reduced the banner height from 300px to 120px 
* reduced the logo size from 40px to 32pd
* changed banner-url to point to a different image


{% codeblock source/css/_variables.styl lang:css %}
// Header
logo-size = 32px
subtitle-size = 16px
banner-height = 120px
banner-url = "images/cat-eyes-and-paw.png"
{% endcodeblock %}


### Previous values


// Header
logo-size = 40px
subtitle-size = 16px
banner-height = 300px
banner-url = "images/banner.jpg"

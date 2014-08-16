---
layout: post
title: "Customise Octopress themes for fun and your profit"
date: 2014-03-12 16:28:28 +0000
comments: true
categories: blogging
tags: [octopress, themes]
---


Octopress themes are stored in the the root folder of your project in a folder called .themes.  If you installed one of the custom themes for Octopress [link], the .themes folder is where the instructions tell you to clone the theme git repository.

Themes can also be installed by passing a parameter to the rake install command. the default theme being “classic”.

Using the .theme folder for your themes helps ensure that your customisations do not get over-written by Octopress updates .

<!-- more-->

## Including font families
You can add hosted fonts just like you do with HTML pages using a link reference.  There are a large number of fonts from Google.

{% codeblock %}
<link href='http://fonts.googleapis.com/css?family=Lato' rel='stylesheet' type='text/css'>
{% endcodeblock %}

I like the Ubuntu font so I add the Ubutu and Ubunto Mono font families using the following code:

{% codeblock %}
<link href='http://fonts.googleapis.com/css?family=Ubuntu+Mono|Ubuntu' rel='stylesheet' type='text/css'>
{% endcodeblock %}

You can select your own fonts to use by visiting [http://www.google.com/fonts/](Google fonts) and adding the font families you like to your collection and Google Fonts will generate the line of code you need to add.


To add Ubuntu fonts directly to your CSS you would use the following:

{% codeblock %}
font-family: 'Ubuntu Mono', sans-serif;
font-family: 'Ubuntu', sans-serif;
{% endcodeblock %}



## Changing Colours

{% codeblock %}
sass/custom/_colors.scss
{% endcodeblock %}

## Example - light colour scheme 

{% codeblock %}
$header-title-font-family:
"Lato",
"Fontdiner Swanky",
"Germania One",
"Poller One",
"Georgia",
"Helvetica Neue",
Arial,
sans-serif !default;
{% endcodeblock %}





## Chainging Style

Change width of the body, the size of the dates and article titles as well as the codeblocks in 

{% codeblock %}
sass/custom/_styles.scss
{% endcodeblock %}

Example

{% codeblock %}
body {
  max-width: 1100px;
}
time {
  font-size: 14px;
}
h1 {
  font-size: 2.2em;
}
section {
  > h1 {
    font-size: 1.5em;
  }
}
codeblock {
    font-size: 1.1em;
}
{% endcodeblock %}


## Icons

[http://www.elegantthemes.com/blog/resources/free-social-media-icon-set](Social media)



## Header images

adding a CSS-styled header image isn’t immediately obvious—at least, not to web-tards like me. My first inclination was to do a bunch of surgery on ~/octopress/source/_includes/custom/header.html and stuff an image in there; that worked, but it didn’t take more than a glance at the CSS behind the Octopress default site to see that the method used there didn’t involve any additional code going into the header section. Plus, just adding an image in there didn’t really fit with the HTML5 fanciness of Octopress and Jekyll—it didn’t resize or reflow as the page was changed.

The key ended up being the realization that the header styling and its reflowing was coded in ~/octopress/sass/base/_layout.scss. True to form, that file has an override in ~/octopress/sass/custom/_layout.scss, and to that I made the following changes:


### Example 

{% codeblock %}
body > header h1 {
      padding-left:2.5em;
      text-align:right;
      @media only screen and (min-width: 432px) {
              text-align:left;
      }
      @media only screen and (min-width: 768px) {
              padding-left:3em;
      }
      @media only screen and (min-width: 992px) {
              padding-left:2em;
      }
}

body > header h2 {
      padding-left:5.62em;
      text-align:right;
      @media only screen and (min-width: 432px) {
              text-align:left;
              padding-left:3.9em;
      }
      @media only screen and (min-width: 768px) {
              padding-left:5em;
      }
      @media only screen and (min-width: 992px) {
              padding-left:2.9em;
      }
}

body > header h1:before {
      content:"";
      position:absolute;
      left:0em;
      right:0;
      top:1.5em;
      height:110px;
      width:110px;
      overflow:hidden;
      text-align:right;
      background-image:url('/images/bigdino-blog-head3.png');
      background-repeat:no-repeat;
      @media only screen and (min-width: 432px) {
              top:.32em;
      }
      @media only screen and (min-width: 768px) {
              left:.75em;
      }
}
{% endcodeblock %}


The changes are divided up into three sections: the first part styles the main title (“Bigdinosaur Blog”), the second styles the subtitle (“Tales of hacking and stomping on things”), and the third places and styles the background image. Each section also contains instructions on how the styles should change as the browser window’s width changes (the lines beginning with @media only).

The most important thing, and the thing that wasn’t obvious to me at first but is actually really obvious in hindsight, is that the initial parameters for each section describe how the thing should look at its smallest, and then each min-width section describes how the thing should look starting at when the browser window is that wide or wider. So, look at header h1. This is the styling applied to the main title in the header. When the browser window is anywhere from 0 to 431 pixels wide, the title should be right-aligned with a bit of padding on its left to keep it from overlapping with the background dinosaur (more on overlapping in a bit). This is how things get displayed on, say, an iPhone.

The instant the browser window is 432 pixels wide—which is the point at which the “Bigdinosaur Blog” text wraps to a single line—the text switches to left-aligned and the amount of padding changes, again to keep it from overlapping with the background dino. Another shift comes again at 768 pixels of width, and then final shift to the title’s most sprawling layout happens at 992 pixels.

The subtitle, styled in the header h2 section, has similar directives—it starts out right-aligned, shifts to left-aligned at a certain point, and the amount of padding around it shifts as the browser window moves. The challenge with the subtitle is that I wanted it to maintain a consistent position relative to the main title, and since I’m doing my spacing using em values (which are themselves relative units), each new width setting required tuning by hand.

The last section places the background image itself. In order to have the most control about where the image appears and where it reflows to, I’ve given it a position:absolute tag, which means that other styled elements ignore the background when figuring out their own layouts—hence all the fiddling about with padding for the header text. Instead of standard image floating behavior, an absolutely positioned image can sit on top of other page elements. This can be used to creative effect, like on the Octopress home page titlebar, but you do have to be mindful with the spacing and padding of your other elements so that they don’t get eaten.

In its most narrow configuration, the background image sits on the far left of the page, with 1.5 ems of space from the top of its section to ensure that it doesn’t poke up past the main title, and with background-repeat:no-repeat set so that it only displays once rather than tiling or repeating itself. I also found that if I didn’t explicitly declare the height and width of the image, it wouldn’t display at all. Finally, there are two width settings that reposition the image as the page widens so that it maintains a visually pleasing position relative to the title.

I mentioned it above, but it’s worth repeating: the values above are what work for my typeface choice and image size, and you will have to tweak your own to taste. Once I had decided exactly what I wanted to do and figured out what files to edit, it took probably an hour of making small changes and previewing and making small changes and previewing over and over again before I was happy with the way things lined up. I spent so much time fiddling, in fact, that I elected to abandon the idea of having the dino pic resize itself. Dinosaurs, I suppose, are meant to be displayed as large as possible, all the time, and would never consent to any funny-business resizing.

http://blog.bigdinosaur.org/changing-octopresss-header/



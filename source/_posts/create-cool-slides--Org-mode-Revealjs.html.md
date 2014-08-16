title: Creating cool slides with Emacs Org-mode and Revealjs
date: 2013-10-03 15:55:00
categories: presenting 
tags: 
- emacs
- orgmode
- revealjs
---

{% img img-thumbnail http://1.bp.blogspot.com/-PLeobToC6lc/TzFJCfBSLPI/AAAAAAAAEbE/zSx1cOgHzZE/s1600/emacs128x128icon.png %}

[Reveal.js](http://lab.hakim.se/reveal-js) has a whole bag of tricks to help you highlight the concepts in your presentations. I'll show you how to write presentations with Emacs & Org-mode that make use of these features, whilest keeping your content as markdown text.  I use a [simple template](https://raw.github.com/jr0cket/slides/gh-pages/template-jr0cket.org) with all the common features there as examples I can copy-n-paste.

I also have a [Github pages site with example slides](http://jr0cket.github.io/slides) I have created.

<!--  more -->

> In a previous article I showed you [how to configure Emacs, Org-reveal and Reveal.js](http://blog.jr0cket.co.uk/2013/09/create-html5-presentations-emacs-revealjs.html) to create HTML5 presentations.


# Creating your presentation

Using Emacs, create a file for your presentation and ensure that the filename has the .org extension.

    C-x C f my-presentation.org

> You can create a new file in Emacs just by opening a file with the new filename.

# Defining the Title Slide

There is a special set of tags you can use to define the title slide, including the theme and style of the overall presentation.

At the top of the `my-presentation.org` file, add `Title`, `Author` and `Email` tags to create the tile slide.

    #+Title: Presenting with Emacs
    #+Author: John Stevenson
    #+Email: @jr0cket

> At first I could not figure out how to add a twitter handle rather than an email address, then I realised I could put anytihng for the email address.  So I just put @jr0cket as the email address and it displays just fine on the rendered slides.


# Setting the Presentation Theme and Slide behaviour

Once you have defined the overall configuration of the presentation, you can add a table of contents or include special formatting libraries like mathjax. 

I never use the table of contents as unless you have a short presentation it will run off the bottom of the screen.  Here is an example of not having a table of contents, but having mathjax available:

    #+OPTIONS: toc:nil reveal_mathjax:t

## Choosing Themes 
You can choose from several built in presentations, including **default**, **beige**, **sky**, **night** (my favorite), **serif**, **simple**, **moon**

You can also make your own theme by creating a new CSS file and defining styles to for that theme.

Define which theme you want using the code:

    #+REVEAL_THEME: night


## Transitions

There are several built in styles of transition effects to move from one slide to another.  I find linear the most pleasing, as it simply slides the content in from the right or bottom to.  Cube is quite a nice rotating cube in the middle of the screen, so you may not get the full benefit of a wide screen display. Zoom is a bit to much for my delicate eyes.

The available tranistions include: **default, cube, page, concave, zoom, linear, fade, none**

Define a transition before any of the slide content (before the first heading) using the code:

    #+REVEAL_TRANS: linear    


# Defining Slides

Each slide is defined by using a `*` character in front of the title.  * is the top-level header for an Org-mode file, so you can collapse each slides content using the TAB key to make it easy to navigate whist creating that content.
 
{% img img-code http://github.com/yjwen/org-reveal/raw/master/images/hlevel.png %}

Using a single `*` for a number of slide titles will create a series of slides you navigate horizontally.  If you define a slide with two `*` characters, then you create slides underneath the slide above.  These slides underneath are navigated vertically, giving a 2 dimensional effect to your presentation.

    * title 1
    * title 2
    ** sub-title 2.1
    ** sub-title 2.2
    * title 3

Each title is a seperate slide, however sub-title 2.1 and 2.1 are slides underneath title 2.  If you are on the title 2 slide and you press the left arrow, you will got to title 3 slide.  If you are on title 2 slide and press the down arrow, you will go to slide heading 2.1.

So with this simple notation you can create a 2-dimentional presentation.


# Adding Slide Content

You can place what ever text you want underneath the heading to for the slide content

    * A very interesting slide

    **This slide is interesting because I am a geek :)
      - bullet points can be added in moderation
      - dont get too carried away with them


# Adding Links

Links to other web pages and resources can be added by simply including a web address in double square brackets:

    [[web address]]   
    [[http://www.google.com]]   


You can also mark text to be a link by placing the link text inside double square brackets as follows:

    [[web address][clickable text]]
    [[http://www.google.co.uk] [Google search engine]]

Any links defined will use the slide style for their colour, font and any animation styles.


# Including Images

You can include images in the presentation using the same kind of syntax for links.  Simply add the relative path of your image within double brackets

    [[./images/org-reveal.png]]

This will display an image from the file org-reveal.png in the images folder.  The same form is also used if you want to include images from web

    [[http://web-address/image-name.png]]

# Slide Colours and Background Images

You can set a different colour or image background for each slide, over-riding the presentation them chosen.  This is set by defining properties for each slide using the `:PROPERTIES:` notation.

To define the colour of the slide background you can use an RGB coluor value or any supported CSS colour format. Here is a simple example of a slide with a red background 

    :PROPERTIES:
    :reveal_background: #FF0000
    :END:

When setting a background image simply provide the relative path to that image. You can also make the background image slide in rather than fade in.

This slide has a background image

    :PROPERTIES:
    :reveal_background: ./logos/github-octopus.png
    :reveal_background_trans: slide
    :END:

## Effects within Slides

You can animate specific parts of each slide using Fragment Options.  You can make your content **grow**, **shrink**, **roll-in** and **fade-out**.  You can also highlight the text in red, green and blue.

* This slide rolls in text line by line:

{% codeblock %}
    #+ATTR_REVEAL: :frag roll-in
    - show bullet-points
    - one by one
{% endcodeblock %}

* Highlight the last bulletpoint in red

{% codeblock %}
    - all these bullet-points
    - show up on the page
    - as soon as its shown

    #+ATTR_REVEAL: :frag highlight-red
    - this last one is then highlighted in red
{% endcodeblock %}

# Generating your Reveal.js presentation

Once you have your presentation written you can generate the presentation with the command

    M-x org-reveal-export-to-html

This command creates a single index.html file that contains your whole presentation, except for any images you have used.  The `.html` file will be have the same name as your org-mode file, so if you created your content in `my-presentation.org` then you will generate `my-presentation.html`.

If your links and images are all correctly referenced in your presentation, then simply opening my-presentation.html file in a browser will show you the end result.

# In Summary

I really liked the presentations generated by Reveal.js and Org-reveal makes is easy to create presentations without having to hand code any JavaScript.  As my presentations are written in plain text then its easy to manage them with Git and collaborate with others via Github.

The next step is to get these presentations in the Cloud.  I could use Heroku, although as this is just a static website and then [**Github pages**](http://pages.github.com/) makes more sense.  I will cover deploying your presentations to Github pages in a follow-on article.

I may also create my own theme by customising one of the existing cascading style sheets (CSS files) should I have issues with projectors but at the moment the night theme works well for me.

Thank you.
[@jr0cket](https://twitter.com/jr0cket)

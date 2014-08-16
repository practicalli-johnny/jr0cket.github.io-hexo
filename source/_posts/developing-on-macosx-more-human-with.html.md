title: Developing on MacOSX is more human with Ubuntu fonts
date: 2013-08-12 20:50:00
categories: ubuntu
tags: 
- ubuntu
- mac
---

As a developer you sit in front of your laptop all day (and night) so why not make it a more human experience by using the set of beautifully clear fonts from Ubuntu. &nbsp;Its really quick and simple to add them to your MacOSX machine (and probably windows), so give it a try.

<!-- more -->

# The Ubuntu font family

{% img img-topic http://3.bp.blogspot.com/-3zqHH9zVZ4s/Ugk10_CFuGI/AAAAAAAAK3Y/l06Tqnyb2o0/s1600/Ubuntu_Font_Family.png %} 

The Ubuntu font family has been professionally designed and is freely available from [font.ubuntu.com](http://font.ubuntu.com/).

The fonts are available in a range of weights as well as different natural languages. &nbsp;As developers there is also a really beautiful mono-type font too called Ubuntu Mono!

Here is a simple example of some Clojure code in the Ubuntu Mono font:

{% img img-code http://2.bp.blogspot.com/-eFL0wzEJQK0/Ugk7322THJI/AAAAAAAAK4k/3xLH4l_82pQ/s1600/ubuntu-fonts-core.clj-example.png %} 

And a further example of some markdown (as used by Github, etc.)

{% img img-code http://2.bp.blogspot.com/-9L5jxUlsc7A/Ugk8HVfwFWI/AAAAAAAAK4s/RD3lwVChM-8/s1600/ubutnu-fonts-index.md-example.png %}

{% img img-code http://2.bp.blogspot.com/--h8jdygzyyI/Ugk3gdRijiI/AAAAAAAAK30/cibAauJPaus/s1600/ubuntu-font-family-list.png %}

# Adding Fonts to MacOSX is a simple drag and drop

Download the Ubuntu fornts zip file and extract it (open the zip file in MacOSX extracts it).

Drag and drop all the files with a .ttf extension (true type font) to the folder containing all the fonts on your Mac:

{% img img-code http://2.bp.blogspot.com/-ieiw0icjWdw/Ugk4JviIQtI/AAAAAAAAK38/Tj8OY04lP9I/s1600/ubuntu-fonts-macosx-library-fonts-path.png %}

Now all your applications on the Mac should be able to use the Ubuntu fonts.

# Tweaking your developer tools

{% img img-topic http://1.bp.blogspot.com/-PLeobToC6lc/TzFJCfBSLPI/AAAAAAAAEbE/zSx1cOgHzZE/s1600/emacs128x128icon.png %}

I use Emacs for most of my development on the Mac, but any app should be able to pick up the Ubuntu fonts you have added. 

I have Emacs configured with the Emacs Live setup, so I simply add the Ubuntu Mono font as the default in the configuration file:

    ~/.live-packs/accountname-pack/init.el

The Emacs Lisp code to set the font to Ubuntu Mono as a font size of 16 (good for demos) is:

    (live-set-default-font "Ubuntu Mono 16")

This code looks much better in Emacs with the new Ubuntu Mono font of course.
{% img img-code http://3.bp.blogspot.com/-Pb4STT7KHYI/Ugk6n6491LI/AAAAAAAAK4U/SZr9rieU8XE/s1600/ubuntu-font-emacs-init.el-example.png %}

# In Summary

Chaning fonts may seem like a small change to make, but anything you can do to make your development environment as enaging and enjoyable as possible is worth doing.  After all I certainly spend a lot of time in my developer environment.

Thank you.
[jr0cket](https://twitter.com/jr0cket)


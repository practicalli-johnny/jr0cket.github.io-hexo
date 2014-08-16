title: Emacs tip - turn Auto Fill off when writing blog posts
date: 2012-02-07 15:55:00
categories: dev-tools
tags: 
- emacs
---

{% img img-thumbnail /images/emacs-logo.png %}

The Fill minor mode will wrap your text so the lines dont become too long.  Whist this is good for code, it puts in hard line breaks for your text which you would have to remove if copied into your blog post.

If you are using emacs to write the content for your blog you probably want to turn off the `Fill` minor mode, as this seems to be on by default when using Emacs 24 and the Emacs starter kit.  

Easiest way for the new starter is to use the right mouse button to select the mode options on the control bar at the bottom of the buffer you are working in.

For those who enjoy the keyboard, fire up the macro `auto-fill-mode` to toggle the mode on and off.

If you would like to have a keyboard oriented lifestyle but are still learning Emacs, press the key combination `Meta-x`, type `auto-fill-mode` and press return.  This toggles the mode, so if its on it switches it of and vice versa.

> On a Linux PC,  Meta-x is the keyboard combination Alt-x, on MacOSX it is Option-x 

Happy Emacs fun!

Thank you.
[@jr0cket](https://twitter.com/jr0cket)

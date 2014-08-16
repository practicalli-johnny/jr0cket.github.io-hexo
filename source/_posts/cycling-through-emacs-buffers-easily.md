title: Cycling through Emacs buffers easily
date: 2014-07-13 12:27:39
categories: dev-tools
tags: emacs
---

{% img img-thumbnail /images/emacs-logo.png %}

Once you have more buffers (files) open than windows in Emacs, then having a quick way to cycle through buffers is invaluable.  Even with 4 windows open, I still find myself using IBuffer, `C-c C-x`, many times.

Sometimes I just want to switch between the current and previous buffer in the same window.  So this is how I tweaked my Emacs configuration (based on Emacs Live) to cycle through buffers.

<!-- more -->

# Cycling through buffers

Emacs has two functions to move through buffers in the current window, `next-buffer` and `previous-buffer`.  These can be called in the usual way using `Meta-x`:

    M-x next-buffer
    M-x previous-buffer

Using these functions is quick than firing up an IBuffer, however if we create some good keybindings then we can cycle buffers even faster.

# Creating keybindings 

I already have several keybindings defined in my Emacs Live personal pack, so I simply add two more keybindings.  The file I put my keybindings in is called `~/.live-packs/jr0cket-pack/config/keybindings.el` and these bindings are loaded by adding the following line to `~/.live-packs/jr0cket-pack/init.el`

    (live-load-config-file "keybindings.el")

The key combination I decided to use was `Ctrl - PageUp` for previous button and `Ctrl - PageDown` for the next buffer.

    ;; Set keybindings for cycling buffers
    (global-set-key [C-prior] 'previous-buffer)
    (global-set-key [C-next] 'next-buffer)

> The PageUp key is referenced by the name prior and the PageDown key is referenced by the name next. 


Thank you.
[@jr0cket](https://twitter.com/jr0cket)

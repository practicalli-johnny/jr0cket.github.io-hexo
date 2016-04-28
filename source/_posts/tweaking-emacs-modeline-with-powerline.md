title: Tweaking Emacs modeline with Powerline
date: 2015-01-28 22:59:23
categories: emacs
tags:
- emacs
- emacslive
- dev-tools
---

{% img img-thumbnail /images/emacs-logo.png %}

  It important to enjoy the development tools you use day after day, so after seeing some of the great looking Emacs modeline customisations, I couldnt resist pimping my modeline (again).
  
  Previously I [tweaked the modeline for Clojure development](http://jr0cket.co.uk/2013/01/tweeking-emacs-modeline-for-clojure.html.html), this time I've added styling to the modeline using [powerline](https://github.com/milkypostman/powerline).  I aim to create a modeline worthy of the rest of the [Emacs Live](http://overtone.github.io/emacs-live/) experience.

<!-- more -->
  
> There are several other versions of powerline listed on the EmacsWiki [powerline](http://www.emacswiki.org/emacs/PowerLine) page.  

## Installing powerline 

  I use Emacs Live as my base configuration for Emacs, so I added the powerline project to my personal configuration `~/.live-packs/jr0cket-pack/`

  First I cloned the powerline Gitub repository into the `lib` folder of my live pack 

```bash
    cd ~/.live-packs/jr0cket-pack/lib
    git clone https://github.com/milkypostman/powerline
```

  Then I created a configuration file for the powerline project
  
```bash
    emacslcient ~/.live-packs/jr0cket-pack/config/powerline.el &
```
  
   Adding the following code to the powerline config file loads the files in `lib/powerline`.  I also state which theme I want to use.
   
```elisp
    (require 'powerline)
    (powerline-default-theme)
```

> There are several other themes avaiable in powerline, including `(powerline-center-theme)` and `(powerline-nano-theme)`

  Finally, I added a function to load the powerline library at startup in my Emacs Live live-pack init.el file, `~/.live-packs/jr0cket-pack/init.el`

```elisp
    (live-load-config-file "powerline.el")
```

  I restarted Emacs and was presented with my new modeline

![Emacs powerline - default theme with my Clojure mode tweaks](/images/emacs-emacs-live-powerline-theme-default.png)

  In full screen with several windows open you can see the difference between active and inactive windows.
  
![Emacs powerline - default theme with active and inactive windows](/images/emacs-emacs-live-powerline-theme-default-fullscreen.png)


## Summary

  The powerline project is an easy way to tweak your modeline into something more stylised.  Next I want to create my own powerline theme to have my own design touches and tailor it more to my needs.

Thank you.
[@jr0cket](https://twitter.com/jr0cket)

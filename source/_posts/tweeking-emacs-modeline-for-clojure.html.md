title: Tweeking Emacs modeline for Clojure Development
date: 2013-01-04 11:01:00
categories: dev-tools
tags: 
- emacs
- clojure
---

{% img img-thumbnail http://1.bp.blogspot.com/-PLeobToC6lc/TzFJCfBSLPI/AAAAAAAAEbE/zSx1cOgHzZE/s1600/emacs128x128icon.png %}

Emacs is fun to configure and if you have the basics of LISP or Clojure then its pretty easy too.  After reading how to [replace the text on the modeline](http://www.masteringemacs.org/articles/2012/09/10/hiding-replacing-modeline-strings/) I decided to customise my mode-line to make it more efficient for Clojure development.  I'll cover how I tweaked the mode line and added this customisation to my [Emacs Live](https://github.com/overtone/emacs-live) based configuration.

<!-- more -->

Instead of a long list of Major and Minor modes that are active, I now have symbols representing those modes.

In the screen-shot you can see I have the following modes running

λ    Clojure mode 
τ    undo-tree
γ    yas
υ    volatile highlights
ηζ  nREPL minor mode
α    auto-complete
φ    paredit

{% img img-code http://3.bp.blogspot.com/-vfMe4acOK5w/UOQuzoDiRBI/AAAAAAAAI3Q/53fhjdSEpHU/s1600/Emacs-clean-mode-line-for-clojure-and-nrepl.png %}

Some other modes are active, but hidden with a null string as I am assuing they are running all the time.

# Configuring Emacs Live

Adding these to the Emacs Live configuration I use is easy, assuming you used the "bro-grammer" script provided by [+Sam Aaron](http://plus.google.com/104881409052969541540).  This script creates a `~/.live-pack` folder where you can add your own keybindings and configuration without it getting hit by Emacs Live updates.

I created a file called `clean-mode-line.el`, based on the one in the Mastering Emacs article.  The file is located in my personal live-packs folder at:

{% codeblock lang:bash %}
~/.live-packs/jr0cket-pack/config/clean-mode-line.el
{% endcodeblock %}

The code for the mode-line tweaks is a Github Gist:

{% gist 4434524 clean-mode-line.el %} 

To use this new mode-line tweak, we ask Emacs Live to load the configuration in clean-mode-lime.el.  To do this, edit the `init.el` file in your live pack

{% codeblock lang:bash %}
~/.live-packs/jr0cket-pack/init.el 
{% endcodeblock %}

Then add the following code:

{% gist 4434605 init.el %} 

# Emacs Tweaked 

When you open a Clojure document, the mode line now displays the major and minor modes as symbols.

{% img img-code http://2.bp.blogspot.com/-yYcO9X9AGWU/UOQu0wmhK3I/AAAAAAAAI3g/rZxXuAQ1Z1E/s1600/Emacs-clean-mode-line-for-clojure.png %}

Starting the Clojure REPL using `M-x nrepl-jack-in` gives you a similar modeline, this time with the major mode being `nrepl-mode`.

{% img img-code http://3.bp.blogspot.com/-vEeUhbx-sWo/UOQu0OplJJI/AAAAAAAAI3Y/wF_I-g9J3rc/s1600/Emacs-clean-mode-line-for-clojure-nrepl.png %}

Switching back to a Clojure file after running nREPL shows `Clojure` as the major mode and `nREPL` running as the minor mode.

{% img img-code http://3.bp.blogspot.com/-vfMe4acOK5w/UOQuzoDiRBI/AAAAAAAAI3Q/53fhjdSEpHU/s1600/Emacs-clean-mode-line-for-clojure-and-nrepl.png %}

## In Summary 

The custom mode line was really easy to set up, thanks to the great info in the [Matering Emacs article](http://www.masteringemacs.org/articles/2012/09/10/hiding-replacing-modeline-strings/).  The tricky part was finding the specific name for the nREPL minor mode that was running.  Other than that it took a couple of minutes, most of which was deciding which symbols to use.  I added a few others at the end of the file in case I change my mind or you want to use something more meaningful to yourself. 

I havent tried this with Swank, but I assume that all it would take is adding of the swank mode to the clean-mode-line.el file.

When I get round to using other modes, I will see if I can add other symbols to my configuration where it makes sense.  Let me know if you find this useful and what symbols you use.   

Thank you.
[@jr0cket](https://twitter.com/jr0cket)

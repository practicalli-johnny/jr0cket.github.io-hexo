title: Emacs Live - instant Clojure development environment
date: 2013-01-14 23:36:00
categories: emacs
tags: 
- clojure
- emacs
- emacslive
- dev-tools
---

{% img img-thumbnail /images/emacs-logo.png %}

Emacs is a really powerful tool for Clojure development, although without a guiding hand it can be a bit of a learning curve.  Using the [Emacs Live](https://github.com/overtone/emacs-live) its really simple to get a fully featured development environment for Clojure.  I will show you how to get Emacs Live installed and how to start using it for Clojure.

<!-- more -->
  I also recommend using [EmacsForOSX](http://emacsformacosx.com/) if you are on a Mac.

{% img img-code http://1.bp.blogspot.com/-lqWITXmJQYY/UPACxNMM3rI/AAAAAAAAI4o/GfP54cumPSQ/s1600/emacs-live-clojure-repl-magit-leiningen-example.png %} 

[Emacs Live](https://github.com/overtone/emacs-live) is a collection of packages for Clojure that include: 

* **Clojure mode** - language support 
* **nREPL** - interactive environment
* **Magit** - manage git repositories 
* **auto-complete** - tab complete expression names &amp; show documentation
* **undo-tree** - undo and redo on steroids with a branching history
* **yasnippets** - abbreviations automatically expand into function templates

# Installing Emacs Live

Emacs Live required Emacs 24 or greater, everything else is self contained.

You could just clone the github repository, but the provided install script makes sure everything is set up correctly and also creates a separate folder for your own personal settings.  This allows you to tweak Emacs Live to your own style without it getting clobbered by any updates.

Run the following in a terminal window (Mac or Linux):

{% gist 4504972 %}

Before anything is installed, the script will move any old Emacs configuration to `~/.emacs.d` to a folder called `~/.emacs.d-old`.

Once all the Emacs Live configuration files are installed, the script asks you if you want to create your own personal configuration.  If so, a new folder will be created called
`~/.live-packs/your-current-username-pack`.

# How to tweak Emacs Live

Its really easy to add your own key bindings and other configurations to Emacs Live, using the personal pack the script created for you.  The personal pack has an `init.el` file in which you can add short simple configurations or load in longer configurations from the `config` or `lib` folders.

## Key bindings
Emacs live makes several changes to the default key bindings of Emacs.  If you want the default  key bindings back then you can simply switch off the Emacs Live key bindings by adding the following to the file `~/.emacs-live.el`

    (live-ignore-packs '(live/bindings-pack))

Alternatively, you can learn to love the Emacs Live bindings, or tweak a few in your own personal pack.  I have added a keybinding for launching the Clojure repl and a pair of key bindings for changing the font size, making it easier to change fonts when giving a demo.

To make the change in my personal pack, I added the following to the file `~/.live-packs/jstevenson-pack/config/bindings.el`

```
;; Simpler key bindings for making text in buffers bigger and smaller
(define-key global-map (kbd "C-+") 'text-scale-increase)
(define-key global-map (kbd "C--") 'text-scale-decrease)

;; Launch Clojure repl via Leiningen - M-x nrepl-jack-in
(global-set-key (kbd "C-c C-j") 'nrepl-jack-in)
```

## Loading in bigger changes

To keep your `init.el` file easy to work with, larger customisations can be defined in their own `.el` files under the config diretory.  Then simply add a line to load in these config files in the file  `~/.live-packs/jstevenson-pack/config/init.el`

See the example where I [tweaked the mode line for Emacs when developing Clojure](http://jr0cket.co.uk/2013/01/tweeking-emacs-modeline-for-clojure.html)

# Upgrading Emacs Live

{% img img-code http://2.bp.blogspot.com/-rWT1D_eoyFU/UPAFbJb-odI/AAAAAAAAI5I/ou7yYkCsw0U/s1600/emacs-live-update-git-fetch.png %} 

As all the configuration files are hosted on Github then a simple `git pull` will bring in any new version.  As the install script clones the github repository, the remote github repository is already set up.

From inside your `~/.emacs.d` folder you can simple do a `git pull` when you know there is an update (notices are posted to the [Emacs Live Google group](https://groups.google.com/forum/?fromgroups=#!topic/emacs-live/)).

If you want to know if you are on the latest version or how many versions you are behind, you can use `git fetch` to get all the latest changes without applying them.  The output of git fetch will list any versions that have been created since you installed.

# Just the Docs

Emacs Live has [documentation](http://overtone.github.com/emacs-live/documentation.html) using the Emacs Live theme on the Github pages for the Emacs Live project.

{% img img-code http://2.bp.blogspot.com/-hiVZZWkLlbg/UPAGL_h-U4I/AAAAAAAAI5Q/J3CzFdhvziw/s1600/emacs-live-docs-themed.png %}

# In Summary

For a developer new to Emacs and Clojure development, getting a great environment to work in is easy.  Learning how to use that environment well will take practice, but this is the case with any tools.  Muscle memory will kick in pretty quickly, so the more you use Emacs the more natural it will feel. 

Thank you.
[@jr0cket](https://twitter.com/jr0cket)

title: "Spacemacs - first impressions from an Emacs driven developer"
date: 2015-08-06 00:24:31
categories: emacs
tags:
- spacemacs
- emacs
---

{% img img-thumbnail /images/emacs-logo.png %}

[Spacemacs](https://github.com/syl20bnr/spacemacs) is a community developed configuration for Emacs that makes it easier for anyone to use this amazing developer tool.  Spacemacs is a well thought out way to apply the vast and diverse power of Emacs, making it more accessible especially to those who are used to using Vi.

Unless you've spent the last few years hand-crafting your own Emacs configuration, then I think you will enjoy Spacemacs.  Here are some reasons why I love Spacemacs as an Emacs user.

<!-- more -->

# Spacemacs is fast

The startup for Spacemacs is really quick, less than 2 seconds, even after adding a whole host of features (layers).  Some of this speed may be due to the lazy loading approach that Spacemacs takes.  In the best tradition of Lisp, some things are only loaded in Spacemacs when they are first used.  For example, when you open a Clojure source code file for the first time, the Clojure layer is loaded and clojure mode is applied.


# Goodbye init.el, hello dotspacemacs

{% img img-topic /images/spacemacs-configure-layers.png %}

The init.el file has long been the entry point for your Emacs configuration with many different ways to setup an Emacs configuration.  With Spacemacs you have the `.spacemacs` file and layers, giving a very structured approach that is easy to follow.

The `.spacemacs` file has three sections

* **dotspacemacs/init** - configuration applied when Spacemacs first starts, eg evil or holy mode(emacs), themes, fonts, full screen, recent files, etc
* **dotspacemacs/layers** - add features to spacemacs using layers, a layer can contain elisp and packages from Melpa/Elpa
* **dotspacemacs/config** - additional layer configuration or your own customisations 

The (emacs) keybindings for dotspacemacs are

`M-m f e d` - open the `~/.spacemacs` file 
`M-m f e R` - reload the configuration from `~/.spacemacs` 

> Some changes in the `~/.spacemacs` file still require a restart of Emacs , especially when pulling in a large number of packages in a layer.

# Navigating with Helm

{% img img-topic /images/spacemacs-helm-file-edit.png %}

Developers drive Emacs with keybindings or use commands via `M-x`.  The more features you add to Emacs, the more keybindings and commands you have at your fingertips.  So to manage all this power, Spacemacs uses Helm to organise these keybindings & commands into groups.  Helm also helps you navigate the file system too, minimising the need to type directory and file names in full.

Commands are grouped by their nemonic character, for example

- `S` - spelling
- `T` - themes
- `a` - applications
- `b` - buffers
- `f` - files
- `g` - git/version control

[Helm](https://github.com/emacs-helm/helm) is an incremental completion and selection
narrowing framework.  Its the central control tower of Spacemacs, it is used to manage buffers, projects, search results, configuration layers, toggles and more.

Once you have learnt the Spacemacs groupings for Helm its really fast to do anything, so take a look at the [Helm documentation wiki](https://github.com/emacs-helm/helm/wiki).

You can still type in command names using `M-x command-name` too, if you know the name of the command you are looking for.

> ido mode is still available in Spacemacs but by default it is over-ridden by Helm.  You can enable ido using `dotspacemacs-use-ido t` in the `dotspacemacs/init` section of `.spacemacs`, however this only replaces a few commands.


# Other features of Spacemacs

{% img img-topic /images/spacemacs-other-features.png %}

- **numbered buffers** - each buffer gets a number in the status bar, allowing you to jump to any buffer using the `M-m` or `SPC` and the buffer number, eg. `M-n 3` jumps to buffer number 3.

- **smartparens and symbol balancing/highlighting** - speeding up typing and reducing errors due to unmatched symbols.  For most symbols in most modes a matching symbol is created.  So if you type `(` then a matching `)` is created too.  If you want to surround some existing text with a symbol pair, then simply highlight the text and press the opening symbol.  A closing symbol is also highlighted when the cursor is at the opening symbol.  Spacemacs also highlights the surrounding symbols, including any parents.  So if you are in a nested list, `(parent code (nested code))`, then if the cursor is on the nested code, both nested & parent symbols are highlighted.

- **smooth scrolling** - unlike the traditional jump-scrolling of Emacs, Spacemacs uses smooth scrolling as you fing in most other text editors.


# Getting started with Spacemacs

Here are a few basic steps I took when starting Spacemacs

## Installing & develop branch

With Emacs 24 installed I simply clone the Spacemacs configuration (first moving any existing Emacs configuration out of the way)

```
git clone --recursive https://github.com/syl20bnr/spacemacs ~/.emacs.d
```

Before running Emacs I switched to the `develop` branch so I would have all the latest additions to Spacemacs (it seems pretty stable so far)

```
git checkout develop
```

Then I just ran Emacs as normal and saw Spacemacs taking shape.  There were a number of Emacs packages to download, so this bit took about a minute.


## Holy mode

I've been using Emacs for several years as my main browser so am very familiar with the Emacs bindings.  So when first starting Spacemacs I naturally chose the **holy** mode (aka Emacs mode)

![Spacemacs - selecting Holy mode](/images/spacemacs-install-holy-mode.png)


## Adding layers

Spacemacs has only a few layers by default so I added auto-completion, clojure, git, html, javascript, markdown, org-mode, syntax-checking and version control to the `dotspacemacs/layers` function in `~/.spacemacs`

After saving the changes to `~/.spacemacs` the configuration was reloaded with `M-m f e R`.  As I installed a lot of packages, I also restarted Emacs once everything had finished.

```lisp
   dotspacemacs-configuration-layers
   '(
     ;; ----------------------------------------------------------------
     ;; Example of useful layers you may want to use right away.
     ;; Uncomment some layer names and press <SPC f e R> (Vim style) or
     ;; <M-m f e R> (Emacs style) to install them.
     ;; ----------------------------------------------------------------
     auto-completion
     better-defaults
     clojure
     emacs-lisp
     git
     html
     javascript
     markdown
     org
     syntax-checking
     version-control
     )
```

Using Helm is an easy way to see what layers are already available in Spacemacs, using the keyboard combo `M-m f e h`.  This gives you a list of all layers and if you hit return on any of the layer names you are taken to the docs for that layer.

![Helm layers](/images/spacemacs-helm-layers-list.png)

You can also create your own layers with `M-m configuration-layer/create-layer`.  See http://thume.ca/howto/2015/03/07/configuring-spacemacs-a-tutorial/ for more info as well as the Spacemacs docs.


## Changing font size

I set the default font to Ubuntu 16, the smallest usable font for my laptop for my own use.

```lisp
   dotspacemacs-default-font '("Ubuntu Mono"
                               :size 16
                               :weight normal
                               :width normal
                               :powerline-scale 1.1)
```

I often share my laptop with others or give a presentation using Emacs.  So I've added two keyboard bindings I commonly used to increase & decrease the font size in the current buffer.  This was added to the `dotspacemacs/config` function in `~/.spacemacs`

```lisp
  (define-key global-map (kbd "C-+") 'text-scale-increase)
  (define-key global-map (kbd "C--") 'text-scale-decrease)
```

## Fullscreen at startup

I like to see Emacs in full screen mode for minimum distraction, so I changed the following option in the `dotspacemacs/init` function of `~/.spacemacs`

```lisp
dotspacemacs-fullscreen-at-startup t
```


# In Summary

I really like the way Spacemacs is organised and have not felt the need to change anything, other than adding a few keybindings.  Its obvious right from the start that Spacemacs has been well thought out.  There is also a great community behind Spacemacs and there is always plenty of help.

There is still a lot to learn to get the most out of Spacemacs, but after a day I am pretty comfortable and productive.  The biggest thing to try is probably the modal editing approach you get with Vi and other eVIl features of Spacemacs.  This could make development with Emacs even faster.

It is well worth reading the [Spacemacs guide](https://github.com/syl20bnr/spacemacs/blob/master/doc/DOCUMENTATION.org), which I found easy to follow.

Thank you.

[jr0cket](http://jr0cket.co.uk)

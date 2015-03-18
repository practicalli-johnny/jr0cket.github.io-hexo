title: custom powerline theme for Emacs modeline
date: 2015-01-30 22:49:53
categories: dev-docs
tags:
- emacs
---

{% img img-thumbnail /images/emacs-logo.png %}

  Continuing my modeline customisation with [powerline](https://github.com/milkypostman/powerline), I wanted to add colour to match the Cyberpunk theme of [Emacs Live](http://overtone.github.io/emacs-live/).  To do this I copied the default them and custmised it, adding colours and chaning the style of seperatr.  Here is how I customised the powerline code to make my own theme.
  
> See how I previously [tweaked Emacs modeline with powerline](http://jr0cket.co.uk/2015/01/tweaking-emacs-modeline-with-powerline.html), as this article carries on from that.  My modeline also includes an earlier [tweak for the minor modes](http://jr0cket.co.uk/2013/01/tweeking-emacs-modeline-for-clojure.html.html).

<!-- more -->

## Modeline seperators as waves

![Emacs - Powerline default arrow seperators](/images/emacs-emacs-live-powerline-theme-default-modeline.png)

  Although the arrows are nice way to seperate the different parts of the modeline, I tried out the different styles.  My favorite was the `wave` style.
  
  To change the style, I edited the `lib/powerline.el` file and change the `powerline-default-separator` to the value to `wave`.  The choice list shows you all the styles of seperator available. 

```elisp
(defcustom powerline-default-separator 'wave
  "The separator to use for the default theme.
  :group 'powerline
  :type '(choice (const alternate)
                 (const arrow)
                 (const arrow-fade)
                 (const bar)
                 (const box)
                 (const brace)
                 (const butt)
                 (const chamfer)
                 (const contour)
                 (const curve)
                 (const rounded)
                 (const roundstub)
                 (const slant)
                 (const wave)
                 (const zigzag)
                 (const nil)))

```

![Emacs - Powerline wave seperators](/images/emacs-emacs-live-powerline-theme-default-modeline-wave.png)
  
> I restarted Emacs each time I changed the seperator style for it to take effect. I am not sure how to update the style without a restart.

## Creating my own theme for Emacs Powerline

  I wanted to change the colours of the modeline to make it more personal to me and also help it stand out between all the text of the buffers.

  Rather than mess up the default theme I simply edited the `lib/powerline/powerline-theme.el` file and copied the default theme completely, called the new theme `powerline-default-theme`.  This allowed me to experiment whilst still having a working reference theme to fall back on.  

  To use my new theme,  I edited the configuration file `~/.live-packs/jr0cket-pack/config/powerline.el` and changed the line defining the theme
   
```elisp
    (require 'powerline)
    (powerline-jr0cket-theme)
```

### Removing modeline information I'm not interested in
  
  There are some of the elements I was not interested in, such as the size of buffer and mule-info. So I edited my jr0cket theme and removed the lines
  
```elisp
    (powerline-buffer-size nil 'l) 
    (powerline-raw mode-line-mule-info nil 'l)
```

### Removing extra spacing

  The default theme adds padding between some elements by adding a space character. 

```elips  
    (powerline-raw " ")
```

   There was aso padding around some elements on the modeline, specifically the line `l` & column `c` numbers and the percentage of buffer above the currently visible text `p`.  The default theme adds numbers in front of these caracters adds padding, which I didnt feel was needed so I deleted those numbers.      

```elisp
    (powerline-raw "%l" face1 'l)
    (powerline-raw "%c" face1 'r)
    (powerline-raw "%p" nil 'r)
```
 

## Changing Colours in the modeline**

  The powerline default theme is very grey, so I wanted to add some colours that would work with the Emacs Live Cyberpunk theme.  Changing colours is done in the `lib/powerline/powerline.el` file.
  
  I changed the text colour using `:foreground`, the background colour with `:background`and made the text bold using `:weight bold`.

  
```elisp
    (defface powerline-active1 '((t (:foreground "#d0d0f0" :background "purple" :inherit mode-line)))
      "Powerline face 1."
      :group 'powerline)
    
    (defface powerline-active2 '((t (:foreground "#63b132" :weight bold :background "black" :inherit mode-line)))
      "Powerline face 2."
      :group 'powerline)
```

## Adding an extra face for the buffer name

  The defalt powerline theme has two faces (styles) for inactive  and active windows - `powerline-active1`, `powerline-active2`, `powerline-inactive1` & `powerline-inactive2`  Different parts of the modeline are assigned to one of the faces and therefore display in different styles.  There are a few parts of the modeline, like the buffer name, that are not assinged to a face and display in the colour of the Emacs theme (Emacs Live)  
  
  I wanted to change the style of the buffer name, so rather than change the Emacs theme I added a third face to the `lib/powerline/powerline-theme.el`.
  
```elisp
    (defface powerline-active0 '((t (:foreground "deep pink" :weight bold :background "black" :inherit mode-line)))
      "Powerline face 0."
      :group 'powerline)
    
    (defface powerline-inactive0
      '((t (:background "black" :weight bold :inherit mode-line-inactive)))
      "Powerline face 0."
      :group 'powerline)
```
  
 I then tried out different colours for the buffer name and settled on the reverse of face0, so updated the `lib/powerline/powerline.el` file by adding an `active0` and `inactive0` configuration as follows:

```elisp
(defface powerline-active0 '((t (:foreground "purple" :weight bold :background "#d0d0f0" :inherit mode-line)))
  "Powerline face 0."
  :group 'powerline)

(defface powerline-inactive0
  '((t (:background "black" :weight bold :inherit mode-line-inactive)))
  "Powerline face 0."
  :group 'powerline)

``` 
  The final active modeline with my theme and colours applied looks very nice and very useful to me

![Emacs - Powerline jr0cket theme fullscreen](/images/emacs-emacs-live-powerline-theme-jr0cket-modeline.png)

  Here is the overal view of Emacs with the jr0cket theme and colours applied.

![Emacs - Powerline jr0cket theme fullscreen](/images/emacs-emacs-live-powerline-theme-jr0cket-fullscreen.png)


## Final version of the jr0cket powerline theme

  Here is the complete code for the `powerline-jr0cket-theme`

``` elisp 
    (defun powerline-jr0cket-theme ()
      "Customisation of the default powerline theme"
      (interactive)
      (setq-default mode-line-format
        '("%e"
          (:eval
           (let* (
             (active (powerline-selected-window-active))
             (mode-line (if active 'mode-line 'mode-line-inactive))
             (face0 (if active 'powerline-active0 'powerline-inactive0))
             (face1 (if active 'powerline-active1 'powerline-inactive1))
             (face2 (if active 'powerline-active2 'powerline-inactive2))
             (separator-left
              (intern
               (format "powerline-%s-%s"
                       powerline-default-separator
                       (car powerline-default-separator-dir))))
             (separator-right
              (intern (format "powerline-%s-%s"
                              powerline-default-separator
                              (cdr powerline-default-separator-dir))))
             (lhs (list (powerline-raw "%*" face0 'l)
                        (powerline-buffer-id face0 'l)
                        (when (and (boundp 'which-func-mode) which-func-mode)
                          (powerline-raw which-func-format face0 'l))
                        (powerline-narrow face0 'l)
                        (funcall separator-left face0 face1)
                        (when (boundp 'erc-modified-channels-object)
                          (powerline-raw erc-modified-channels-object face1 'l))
                            (powerline-major-mode face1 'l)
                            (powerline-process face1)
                            (powerline-raw " " face1 'r)
                            (powerline-minor-modes face1 'l)
                            (powerline-narrow face1)
                            (funcall separator-left face1 face2)
                            (powerline-vc face2 'r)))
             (rhs (list (powerline-raw global-mode-string face2 'r)
                        (funcall separator-right face2 face1)
                        (powerline-raw "%l" face1)
                        (powerline-raw ":" face1)
                        (powerline-raw "%c" face1)
                        (funcall separator-right face1 face0)
                        (powerline-raw "%p" face0)
                        (powerline-hud face2 face1))))
             (concat (powerline-render lhs)
                     (powerline-fill face2 (powerline-width rhs))
                     (powerline-render rhs)))))))
```

# Summary 

  [Powerline](https://github.com/milkypostman/powerline) is a really nice way to add that extra touch to the Emacs experience.  Its also pretty easy to configure to give you your own personalised look to the Emacs modeline.  Let me know if you have any interesting customisations to your Emacs setup.
  
Thank you.
[@jr0cket](https://twitter.com/jr0cket)

title: "spacemacs for clojure development with emacs - configure clojure"
date: 2015-09-07 17:54:45
categories: dev-tools
tags:
- clojure
- emacs
- spacemacs
---

{% img img-thumbnail /images/emacs-logo.png %}

Adding the Clojure layer to Spacemacs provides great support for the language via [CIDER](https://github.com/clojure-emacs/cider), Clojure-mode, clj-refactor and lots of useful tools.

The **Clojure** layer also adds to the **auto-completion** layer, providing matches for anything currently defined in the current namespace.  The yasnippets package also allows you to expand shortcuts for common Clojure code structures, eg. def, defn, let, require.

<!-- more -->

# Adding Clojure support

Clojure support in Spacemacs is configured by adding the **clojure** layer.  Edit `./spacemacs` and add `clojure` to the list of layers defined in ``dotspacemacs-configuration-layers` function

```lisp
(dotspacemacs-configuration-layers '(clojure)
```

> For an example, see my [spacemacs configuration on github](https://github.com/jr0cket/spacemacs-config). Please note that there are more configuration options added to this file than required for Clojure, only add the ones you understand.

Restarting Emacs will download by the related packages for Clojure.

> You can also use `SPC f e R` (evil mode) or `M-m f e R` (holy mode) to reload the Spacemacs configuration and download packages, however for a big layer I have found a restart of Emacs is needed to load in all the new configuration.


## Configure Pretty symbols

You can configure the Clojure layer to use pretty symbols to represent a few things in Clojure, such as:

```clojure
(λ [a](+ a 5)) ;; anonymous function (fn ...)
ƒ(+ % 5)       ;; anonymous function shorthand #(...)
∈{2 4 6}       ;; set #{...}
Ƥ              ;; partial function (partial ...)
```

To enable this feature, edit the `./spacemacs` file and add the following snippet to the `dotspacemacs/config` function:

```lisp
(setq clojure-enable-fancify-symbols t)
```

# Configure Leiningen

Install Leiningen using the instructions on [Leiningen.org](http://leiningen.org).

Edit the Leiningen profile configuration for your useer, eg. `~/.lein/profiles.clj` and add the following plugins and dependencies:

```clojure
{:user {:plugins      [[cider/cider-nrepl "0.10.0"]
                       [refactor-nrepl "1.2.0"]]
        :dependencies [[alembic "0.3.2"]
                       [org.clojure/tools.nrepl "0.2.12"]]}}
```

> Check for the latest versions of [cider-nrepl](https://clojars.org/cider/cider-nrepl), [refactor-nrepl](https://clojars.org/refactor-nrepl), [alembic](https://clojars.org/alembic) & [tools.nrepl](https://github.com/clojure/tools.nrepl)

The `cider-nrepl` plugin should match the version of CIDER used in Spacemacs, found by using  `M-x cider-version`. You will see a warning message in the REPL buffer if the versions do not match, for example:

![Clojure REPL - CIDER and cider-nrepl version mis-match](/images/spacemacs-cider-nrepl-mismatch.png)

# Summary

Now you have the Clojure layer and Leiningen configured so you can create your Clojure apps with ease.  Next time we will show how to use the REPL to evaluate code, giving you almost instant feedback on what you have created.

Thank you
[jr0cket](https://twitter.com/jr0cket)

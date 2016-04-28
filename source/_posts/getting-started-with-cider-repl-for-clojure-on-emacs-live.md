title: getting started with cider repl for clojure on emacs live
date: 2015-01-21 11:07:17
categories: emacs
tags:
- clojure
- emacs
- dev-tools
---
{% img img-thumbnail /images/clojure-cider-logo.png %}

  [CIDER](https://github.com/clojure-emacs/cider) is the Clojure IDE and REPL for Emacs.  It is built on top of nREPL, the Clojure networked REPL server and replaces the direct use of nREPL in Emacs.

  In this article we are using CIDER that is packaged in Emacs Live, a very complete, well organised and extensible configuration for Clojure and many other things in Emacs.

<!-- more -->
  
  CIDER includes the standard interactive code evaluation developers are used to.  There are also many other features that I want to explore further, including error and warning highlighting, human-friendly stacktraces, smart code completion, definition & documentation lookup, value inspector & function tracing, interactive macroexpansion, [Grimoire](http://conj.io/) integration, `clojure.test` integration, classpath browser, namespace browser, nREPL session management, scratchpad, minibuffer code evaluation, integration with [company-mode](http://company-mode.github.io/) and [auto-complete-mode](https://github.com/clojure-emacs/ac-cider)

## Emacs Live 

  CIDER is now the default in the latest version of [Emacs Live](http://overtone.github.io/emacs-live/), so there no set up to do if you already have the latest version.  If you need to update, or are not sure you are on the latest version of Emacs live, simply run a _git pull_ from within `~/.emacs.d` directory:
  
    git pull origin master
  
  If you dont have Emacs Live, you can install it from the [Emacs Live Github repository](https://github.com/overtone/emacs-live) and either clone the repository into `~/.emacs.d` (moving or deleting any existing directory) or preferably use the install script that also sets up a `~/.live-packs` extension directory.
  
```bash
    bash <(curl -fksSL https://raw.github.com/overtone/emacs-live/master/installer/install-emacs-live.sh)
```  

## Leiningen configuration

  CIDER requires the use of [nREPL middleware](https://github.com/clojure-emacs/cider-nrepl) between Emacs and Leiningen.  For example, when you run CIDER `M-x cider-jack-in` in Emacs it calls Leiningen to start the REPL.  So you need to add a plugin to your Leiningen configuration.
  
  Edit the `~/.lein/plugings.clj` file (or create this file if it does not exist yet) and add the `[cider/cider-nrepl "0.8.1"]` plugin.  The `~/.lein/plugings.clj` should look similar to this:
  
```clojure
    {:user {:plugins [[lein-pprint "1.1.1"]
                      [cider/cider-nrepl "0.8.1"]]}}
```

> You can find the available versions of the [cider-nrepl plugin on Clojars.org](https://clojars.org/cider/cider-nrepl).  The plugin version should be the same version of CIDER you are using in your Emacs configuration, which at the time of writing was 0.8.1.

## Running CIDER in Emacs

  Either create a new Clojure project using `lein new my-project-name` or open an existing project in Emacs (either the `project.clj` file or a `.clj` file from `src/my-project-name/`).
  
  With your cursor in the Clojure file buffer, run CIDER using the keybinding `C-c M-j` or the emacs command 
  
    M-x cider-jack-in

![Emacs Live - CIDER jack in - C-c M-j](/images/emacs-cider-started.png)

> Alternatively, you could run a REPL using `lein repl` on the command line and connect to that REPL using `C-c M-c` or `M-x cider`.  You will be prompted for the connection details of the running repl, ie. host, port.


## Using CIDER in Emacs

  There are a number of [Cider keyboard shortcuts (keybindings)](https://github.com/clojure-emacs/cider#keyboard-shortcuts) already defined, here are some of the most common ones I use:

* `C-c C-e` - evaluates the form immediately before the cursor and shows the result in the minibuffer.  So place your cursor right after the closing parentheses `)` of your expression, hit the keybinding and see the minibuffer for the result.

![Emacs Live - CIDER eval form with result in minibuffer - C-c C-e](/images/emacs-cider-eval-expression-minibuffer.png)

* `C-c M-e` - the same as above except the result is sent to the REPL

![Emacs Live - CIDER eval form with result in the REPL - C-c M-e](/images/emacs-cider-eval-expression-repl.png)

* `C-c C-k` - evaluate the whole buffer.  So with the cursor in a Clojure source file, all the forms / expressions are evaluate as if the code was loaded in from scratch.

* `C-c C-d d` - show the documentaion as you would with `(doc function-name)`.  Place the cursor over a function name, hit the keybinding and see the documenation for that funtion.  This also works inside the REPL buffer, so no need to use `(doc)`, which is not loaded by default. 

* `C-c M-n` - switch to namespace of current Clojure buffer.  So with the cursor in a Clojure source file, hit the keybinding and your REPL buffer will now be in the namespace for that Clojure code.

![Emacs Live - CIDER change to namespace of current Clojure code - C-c M-n](/images/emacs-cider-namespace-change.png)

> Changing into a namespace does not automatically evaluate the code in that namespace, so evaluate the whole buffer `C-c C-k` or evaluate specific expressions (forms) `C-c M-e`.  Once evaluated, you can evaluate that code in the REPL.

* `M->` or `M-x cider-jump-to-var` prompts you for a var, a function `(defn)` or symbol name `(def)` and moves the cursor to its definition.  If the cusor is already on a matching name the the cursor jumps straight to that definition.

* `C-c C-q` or `M-x cider-quit` - close the REPL and its associated buffer.
 
  There are many more things you can do within Clojure files and the REPL, so take a look at the [Cider keyboard shortcuts (keybindings)](https://github.com/clojure-emacs/cider#keyboard-shortcuts) once you have the basics mastered.


## Further reading 

  Some further reading around CIDER:
  
* [Cider keyboard shortcuts (keybindings)](https://github.com/clojure-emacs/cider#keyboard-shortcuts)
* [Clojure on Emacs - A CIDER workflow hack](http://blog.jenkster.com/2013/12/a-cider-excursion.html) - Kris Jenkins

  Have fun and be productive with CIDER, Emacs and Clojure.  If you have any other suggestions on getting them most out of these tools, please let me know.

Thank you.
[@jr0cket](https://twitter.com/jr0cket)

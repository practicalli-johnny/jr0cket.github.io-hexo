title: "Clojure with Spacemacs: coding with the REPL"
categories: devtools
tags:
- clojure
- spacemacs
- cider
---

Discover how to use (dynamic / live coding / whole program / REPL driven Development) with Clojure and Spacemacs.
- fast feedback
- quick to code out a design
- test your code by running it as you go along and run unit tests too

> Previously I covered how to [configure Spacesmacs for Clojure development](http://jr0cket.co.uk/)


With a Clojure file open in Emacs, launch the repl using either

* `M-x cider-jack-in`
* `C-c M-j`
* run a repl with `lein repl` and in emacs connect with `M-x cider-connect`

> See a list of keybindings and the functions they call by selecting a Clojure buffer and calling describe-mode using `M-x describe-mode`.  This opens another buffer and shows all the keybindings for all the active modes, including CIDER.  There are many minor modes active, so search for the Cider keybindings using `C-s cider`

;; in the previous article suggest the REPL configuration not be part of the leiningen configuration unless this code is only destined to be closed. its a tool specific configuration so doesnt really belong in the project.clj.  a project should not be dependent on a specific set of versions of tooling and any minimum version should be defined in the project documentation


# Coding in the REPL


## Re-evaluate everything with refresh

`(refresh)`



    The refresh function will scan all the directories on the classpath for Clojure source files, read their ns declarations, build a graph of their dependencies, and load them in dependency order.

https://github.com/clojure/tools.namespace#reloading-code-usage

It doesn't seem to remove the vars declared in the user namespace, which I've typed into the REPL, but it does:

    ...unload (remove) the namespaces that changed to clear out any old definitions.



C-c C-x 	Reload all modified files on the classpath. If invoked with a prefix argument, reload all files on the classpath. If invoked with a double prefix argument, clear the state of the namespace tracker before reloading.

[TODO: give an example of a prefix argument and double prefix argument]


## Clearing the REPL

`C-c M-o` clears the whole buffer window with the function `nrepl-clear-buffer`

`C-c C-o` clears the last imput, i.e if the last result produced a lot of results, eg. if you called the `range` function without any constraint 

> You can limit the output displayed in the repl with ....

## Reloading the REPL




# Things not working in spacemacs

## unbound keybindings 
C-c M-d -- should display default REPL connection details



# Reference

## Cider minor mode (indicator cider[clj:clojure-through-code@:56657]):
Minor mode for REPL interaction from a Clojure buffer.

```
key             binding
---             -------

C-c             Prefix Command
C-x             Prefix Command
ESC             Prefix Command

C-x C-e         cider-eval-last-sexp

C-M-i           complete-symbol
C-M-x           cider-eval-defun-at-point
M-,             cider-pop-back
M-.             cider-find-var

C-c C-b         cider-interrupt
C-c C-c         cider-eval-defun-at-point
C-c C-d         cider-doc-map
C-c C-e         cider-eval-last-sexp
C-c C-f         cider-pprint-eval-defun-at-point
C-c C-k         cider-load-buffer
C-c C-l         cider-load-file
C-c RET         cider-macroexpand-1
C-c C-n         cider-eval-ns-form
C-c C-o         cider-find-and-clear-repl-output
C-c C-p         cider-pprint-eval-last-sexp
C-c C-q         cider-quit
C-c C-r         cider-eval-region
C-c C-t         cider-test-show-report
C-c C-u         cider-undef
C-c C-w         cider-eval-last-sexp-and-replace
C-c C-x         cider-refresh
C-c C-z         cider-switch-to-repl-buffer
C-c ESC         Prefix Command
C-c ,           cider-test-run-tests
C-c C-,         cider-test-rerun-tests
C-c C-.         cider-find-ns

C-c M-,         cider-test-run-test
C-c M-.         cider-find-resource
C-c M-:         cider-read-and-eval
C-c M-d         cider-display-connection-info
C-c M-e         cider-eval-last-sexp-to-repl
C-c M-i         cider-inspect
C-c M-m         cider-macroexpand-all
C-c M-n         cider-repl-set-ns
C-c M-p         cider-insert-last-sexp-in-repl
C-c M-r         cider-rotate-default-connection
C-c M-s         cider-selector
C-c M-t         Prefix Command
C-c M-z         cider-load-buffer-and-switch-to-repl-buffer

C-c M-t n       cider-toggle-trace-ns
C-c M-t v       cider-toggle-trace-var

C-c C-d C-a     cider-apropos
C-c C-d C-d     cider-doc
C-c C-d C-j     cider-javadoc
C-c C-d C-r     cider-grimoire
C-c C-d A       cider-apropos-documentation
C-c C-d a       cider-apropos
C-c C-d d       cider-doc
C-c C-d h       cider-grimoire-web
C-c C-d j       cider-javadoc
C-c C-d r       cider-grimoire
```



# Clojure mode defined in `clojure-mode.el':
Major mode for editing Clojure code.

```
key             binding
---             -------

C-c             Prefix Command
ESC             Prefix Command
C-:             clojure-toggle-keyword-string

C-c ESC         Prefix Command

C-M-q           prog-indent-sexp

C-c M-J         cider-jack-in-clojurescript
C-c M-c         cider-connect
C-c M-j         cider-jack-in
```



# Testing

M-RET t a | cider-test-run-all-tests | run all tests
M-RET t r  -- re-run only failing tests

Once the tests have been run, a new buffer window appears with a test report

![Cider test report][]

You also get an pass or fail indicator in the mini-buffer, including the namespace being tested.

If there are failing tests, then the assertions (is ...) functions of the failing tests are highlighted

![Cider test report][]


As well as calling tests via Cider test, you can also run tests manually when the REPL is running.  Edit your test code for your project and add one (or both) of the run test functions:

;; Run tests in current namespace 
#_(run-tests)

;; Run tests across all namespaces of this project
#_(run-all-tests)

In this example the run-test functions have been commented out using the Clojure comment macro.  This prevents these functions being called when the project is run, i.e via lein run and allows the tests to be run manually (assuming a Clojure REPL is connected to Emacs)


## Testing on the command line

Running…

```
lein test
```
…shows you that the project starts with one failing test, which expects false to be true—not one that I’m particularly keen to make pass, but a good example nonetheless.

It’s pretty trivial to run tests this way, but of course the JVM startup time makes it much more efficient to run tests in a different way:

```
lein interactive
lein> test
```
Leiningen’s interactive mode is a pretty sweet way to avoid taking the JVM startup time hit for every test run, but it’s a bit of a double-edged sword: you might get falsely passing test runs, because of the fact that JVM classes will stick around in memory even after you delete their associated functions.

Just be sure to run tests occasionally outside of interactive mode, and you’ll be sure to catch errors like this quickly. 


# Snippets


Snippets can also be included in the auto-complete menus, this is my prefered way to use them.  It also save you remembering the default snippet or having to set your own (I find the default keybinding hard to remember)

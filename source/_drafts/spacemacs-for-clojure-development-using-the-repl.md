title: "spacemacs for clojure development with emacs - configure clojure"
categories: dev-tools
tags:
- clojure
- emacs
- spacemacs
---

{% img img-thumbnail /images/emacs-logo.png %}

Previously we configured the Clojure layer in Spacemacs, this time we will show how to use the REPL to evaluate your code almost instantaneously.



# Starting a REPL

You can start a Clojure REPL within Emacs for any Leiningen created project (there should be a `project.clj` file in the root of the project directory).

> To create a new Clojure project within Emacs, use `M-x eshell` and run the `lein new project-name` command

Open either the `project.clj` file or any other `*.clj` source file in a buffer, `C-x C-f`.  From that buffer, start a REPL using either

* `C-c M-j` via clojure-mode
* `M-m m i`/ `SPC m i` -  helm, major-mode, i for clojure-jack-in) [BUG: no `m` major mode menu with `M-m`]
* `M-RET s i` - spacemacs major mode + cider (sider) + jack-in (in)
* `M-x cider-jack-in`

With a Clojure buffer highlighted, you can use `C-c` to show a menu of CIDER commands available via the major-mode.

# REPL driven development

Once connected to a running REPL you can interact with Clojure dynamically.  You can evaluate all the clojure in the current buffer, or just a single expression.


## Evaluate a Clojure file

You can evaluate all the code in a Clojure file by opening it and evaluating the buffer

* `C-c C-k` - clojure-mode, cider, (k)compile
* `M-m m e b` / `SPC m e b` - holy / evil helm, evaluate, buffer
* `M-RET e b` spacemacs major-mode, evaluate, buffer
* `M-x cider-evaluate-buffer`

> As Clojure evaluates code in order, then make sure any function call comes after its declaration.

## Evaluating an expression

You can evaluate just an expression by placing the cursor immediately after the closing parens and using either:

* `C-x C-e` clojure-mode
* `SPC m e e` holy / evil mode, major-mode, evaluate, expression

To show the result in a new buffer, you can use the command

* `M-x cider-pprint-evaluate-last-sexp`

Press `q` to close the new buffer (when active)

Other evaluation keybindings include

* `M-m m e b` -  eval buffer
* `M-m m e e` -  eval last sexp
* `M-m m e f` -  eval function at point
* `M-m m e r` -  eval region
* `M-m m e w` -  eval last sexp and replace with result 

# Navigation

The usual Emacs navigation can be used via Control (character) & Meta (word) based movements using forward (f), back (b), next (n), previous (p).

As Clojure expressions form a tree structure, you can navigate very quickly along the different expressions in your code. 

`M-x sp-forward-sex`


# Editing clojure code

Spacemacs uses **smartparens** minor mode to help you manage your Clojure code.  As all your code is surrounded by one kind of delimiter, eg. `( [ { "`, then smartparens automatically adds the matching closing delimiter when you type an opening delmiter.  So if you type `(` to create a list, then smartparens adds `)` immediately after, leaving the cursor inbetween the two.

## Deleting things

You can delete delimiters at any time, unless you enable smartparens strict mode

`C-k` delete to end of line - the usual emacs `M-x kill-line`

`M-x sp-kill-hybrid-sexp` to ensure you do not delete delimiters that would break code

`C-M-k` or `M-x sp-kill-sexp` kill the current expression - this is how paredit works

`M-x sp-kill-symbol`
`M-x sp-kill-word`

`M-x sp-delete-char` - deleted the current character unless its a delimiter (paredit style)


## Copy

`M-x sp-copy-sexp` copy the current expression, place the cursor on either the opening or closing delimiter


## slurping & barfing


`M-m J` split sexpression 



## Docs & other keybindings 

This is still work in progress

| Key Binding | Description    |
| ----------- | -------------- |
| `SPC m h h` | cider doc      |
| `SPC m h g` | cider grimoire |
| `SPC m h j` | cider javadoc  |



** Goto

| Key Binding | Description   |
| ----------- | ------------- |
| ~SPC m g g~ | goto var      |
| ~SPC m g e~ | goto error    |
| ~SPC m g r~ | goto resource |
| ~SPC m g b~ | go back       |

** REPL

| Key Binding | Description                                                  |
| ----------- | ------------------------------------------------------------ |
| ~SPC m s b~ | send and eval buffer in REPL                                 |
| ~SPC m s B~ | send and eval buffer and switch to REPL in =insert state=    |
| ~SPC m s c~ | connect to REPL (cider-connect)                              |
| ~SPC m s e~ | send and eval last sexp in REPL                              |
| ~SPC m s E~ | send and eval last sexp and switch to REPL in =insert state= |
| ~SPC m s f~ | send and eval function in REPL                               |
| ~SPC m s F~ | send and eval function and switch to REPL in =insert state=  |
| ~SPC m s i~ | start REPL (cider-jack-in)                                   |
| ~SPC m s n~ | send and eval ns form in REPL                                |
| ~SPC m s N~ | send and eval ns form and switch to REPL in =insert state=   |
| ~SPC m s q~ | kill REPL (cider-quit)                                       |
| ~SPC m s r~ | send and eval region in REPL                                 |
| ~SPC m s R~ | send and eval region and switch to REPL in =insert state=    |
| ~SPC m s s~ | switch to REPL                                               |

** Tests

| Key Binding | Description                        |
| ----------- | ---------------------------------- |
| ~SPC m t a~ | run all tests in namespace         |
| ~SPC m t r~ | re-run test failures for namespace |
| ~SPC m t t~ | run test at point                  |

** Debugging

| Key Binding | Description                    |
| ----------- | ------------------------------ |
| ~SPC m d b~ | instrument expression at point |
| ~SPC m d i~ | inspect expression at point    |

** Refactoring

| Key Binding   | Description               |
| ------------- | ------------------------- |
| ~SPC m r a d~ | add declaration           |
| ~SPC m r a i~ | add import to ns          |
| ~SPC m r a m~ | add missing libspec       |
| ~SPC m r a p~ | add project dependency    |
| ~SPC m r a r~ | add require to ns         |
| ~SPC m r a u~ | add use to ns             |
| ~SPC m r c c~ | cycle coll                |
| ~SPC m r c i~ | cycle if                  |
| ~SPC m r c n~ | clean ns                  |
| ~SPC m r c p~ | cycle privacy             |
| ~SPC m r d k~ | destructure keys          |
| ~SPC m r e f~ | extract function          |
| ~SPC m r e l~ | expand let                |
| ~SPC m r f u~ | find usages               |
| ~SPC m r h d~ | hotload dependency        |
| ~SPC m r i l~ | introduce let             |
| ~SPC m r m f~ | move form                 |
| ~SPC m r m l~ | move to let               |
| ~SPC m r p c~ | project clean             |
| ~SPC m r p f~ | promote function          |
| ~SPC m r r d~ | remove debug fns          |
| ~SPC m r r f~ | rename file               |
| ~SPC m r r l~ | remove let                |
| ~SPC m r r r~ | remove unused requires    |
| ~SPC m r r s~ | rename symbol             |
| ~SPC m r r u~ | replace use               |
| ~SPC m r s n~ | sort ns                   |
| ~SPC m r s p~ | sort project dependencies |
| ~SPC m r s r~ | stop referring            |
| ~SPC m r t f~ | thread first all          |
| ~SPC m r t h~ | thread                    |
| ~SPC m r t l~ | thread last all           |
| ~SPC m r u a~ | unwind all                |
| ~SPC m r u w~ | unwind                    |

** Reformatting

- Forms currently handled:
  - let
  - when-let
  - if-let
  - binding
  - loop
  - with-open
  - literal hashes {}
  - defroute
  - cond
  - condp (except :>> subforms)
  
More info at [[https://github.com/gstamp/align-cljlet][align-cljlet]].

| Key Binding | Description           |
| ----------- | --------------------- |
| ~SPC m f l~ | reformat current form |


For example, say you have a let binding that has 2 pairs of unequal lenghts

```
(let [fish 1
      rabbit 2
      cat 3])
```

Placing the cursor in the let binding and using `SPC m f l` or `M-x align-cljlet` or `M-RET f l `

```
(let [fish   1
      rabbit 2
      cat    3])
```

# Snippets

To save typing of common code you can use yas-snippets

** Yasnippet

| Key Binding | Description                                                    |
| ----------- | --------------------------------------------------------------- |
| `M-/`       | Expand a snippet if text before point is a prefix of a snippet |
| `SPC i s`   | List all current yasnippets for inserting                      |
| `M-m i s`   | List all current yasnippets for inserting                      |

** Auto-yasnippet

| Key Binding | Description                                                               |
|-------------+---------------------------------------------------------------------------|
| `SPC i S c` | create a snippet from an active region                                    |
| `SPC i S e` | Expand the snippet just created with `SPC i y`                            |
| `SPC i S w` | Write the snippet inside =private/snippets= directory for future sessions |


|       |      |       |     |        |            |      |           |       |       |
| ----  | ---- | ----- | --- | ------ | ---------- | ---- | --------- | ----  | ----- |
| bench | defm | deft  | for | import | map        | ns   | print     | test  | when  |
| bp    | defn | doseq | if  | is     | map.lambda | opts | reduce    | try   |  whenl|
| def   | defr | fn    | ifl | let    | mdoc       |   pr |   require |   use |       |


## Adding your own clojure snippets



# clj-refactor



# Documentation

Classic cider bindings

`C-c C-d d` show the docs for any function (or macro & special form), as well as Javadocs for Java

`M-RET h h` - clojure documentation
`M-RET h j` - javadoc docu
  * mentation
`M-RET h g` - clojure grimore documentation


# In Summary


* [Spacemacs Rocks](http://spacemacs.brianthicks.com/) - handy tips every Tuesday & Thursday


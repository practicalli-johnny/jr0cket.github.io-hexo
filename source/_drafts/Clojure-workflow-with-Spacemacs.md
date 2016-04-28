title: "Clojure workflow with Spacemacs"
date: 2016-03-01 23:19:54
categories: 
tags: 
---


## Open a Clojure file

`M-m f f`


## Start a REPL

`M-RET s i`
`SPC m s i`

## Evaluate the whole buffer

Emacs mode
`M-RET e b`

Vi mode
`SPC m e b`

Classic Emacs
C-c C-k


## Evaluate an expression

Move the cursor to the end of an expression, after the closing parenthesis `)`

M-RET e e

## Evaluate an expression and replace it with its value

`M-RET e w`


## Documentation

`M-RET h h`  ;; cider doc
`M-RET h g`  ;; grimore docs
`M-RET h j`  ;; java docs


## Debugging

`M-RET d b`  ;; debug function
`M-RET d i`  ;; cider-inspect ??

Thank you.
[@jr0cket](https://twitter.com/jr0cket)

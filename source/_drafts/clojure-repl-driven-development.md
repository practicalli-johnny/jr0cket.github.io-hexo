title: "Clojure REPL Driven Development"
date: 2015-08-09 13:41:07
category: dev-tools
tags:
- clojure
- emacs
---



Using a REPL or REPL-connected editor to develop and debug code

"tightens the feedback loop like nothing I've ever seen," which I think is descriptive yet still not particularly helpful.

https://www.youtube.com/watch?v=_B_4vhsmRRI

I also found Jay Field's RDD post which I had read before,

but sort of just states the same thing I already said.

Some examples of techniques that aren't possible without a REPL

1. (def *foo* (arbitrary expression))

Modify a function definition to capture a var and then run what you're working on to have a value you can interact with as you continue to develop. This is also incredibly useful when debugging code because you can capture the args to a function and then work with and inspect them offline.

If you need to capture something in a let chain you can `_ (def …)` handily.

2. Interactively modify a function definition when you believe you have a solution and verify that it works immediately (no release!)

I think the thing that I find hard to express about this is that all the advice boils down to "You have the entirety of your language instantly at your disposal to debug and develop anything" which is both true and not very helpful if the tightest feedback loop you've used is TDD.



# Tips

## re-evaluate as you go



## Using let

Create a let when you want to explore some evaluation



## multiple versions of functions

how to use different versions effectively ?

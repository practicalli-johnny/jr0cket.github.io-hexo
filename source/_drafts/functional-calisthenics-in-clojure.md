title: "functional calisthenics in clojure"
date: 2016-03-02 18:17:47
categories: 
tags: 
---





# Ninja Ferret content

 Object Calisthenics helps people to become better Object-Oriented programmers and as someone new(ish) to the functional world I wondered if there were an equivalent set of rules that would help me become a better functional programmer, so I asked the people at SoCraTes UK 2015:

* Side effects can only occur at the top level
* No mutable state
* Expressions not statements
* Functions should have 1 argument
* No explicit recursion
* Maximum type-level abstraction
* Always use infinite sequences
* No "if"
* Name everything
* Use intermediates
* Don't abbreviate

Want to read more?

What are Functional Calisthenics? They are derived from Object Calisthenics, these rules that you can apply to make your object-oriented code better by applying strict rules in what you can and cannot do. These strict rules force you to think differently about how to write your code, e.g. the rule No getters of setters will often lead to people thinking If I can't get at the internal state using a getter, how can I test that the current state is correct? I was wondering whether there was something similar that I could use as a training exercise to improve my functional programming and escape an "object-oriented mindset".

So, I asked the wonderful community at the SoCraTes UK 2015 conference about them, there was a huge amount of interest and a lot of people enthusiastically helped to come up with these initial thoughts on our Functional Calisthenics.
Side effects can only occur at the top level

We want the majority of our code to be pure functions and in order for that to be the case they cannot depend on anything that is impure. This means we should pull the impure functions up to the top level and isolate them as much as possible from the rest of the code. This can include:

* User interaction
* Database access
* API calls

No mutable state

This is very close to the Side effects can only occur at the top level rule but we can go further than just creating pure functions, we don't want to mutate state within a function either, e.g. do not re-use variables (if your language allows) as this has a negative impact on code readability and any mutable state could potentially result in an unintended consequence.
Expressions not statements

This is a kind of extension of the No mutable state rule, if we are calling a function that does not return anything then we are probably expecting that some mutable state will be changes as a part of this call and the function will not be pure. If we are aiming for purity then we should only be using functions that take return values.
Functions should have one argument

This is one that is probably causing a fair amount of debate, but we should be using restricting the number of arguments that a function can take, a function with a large number of arguments smells of a single responsibility principle violation. Currying provides us with the ability to reduce long argument lists to a series of functions that all take one parameter.
No explicit recursion

Prefer separating the method of recursion away from the logic that you are trying to execute.
Maximum level of abstraction

Functions should take the highest level of abstraction possible, e.g. if List is a special case of Enumerable then the function should take Enumerable.
Use infinite sequences

If you function takes, or returns, a sequence of data then write the function in a way that does not exclude infinite sequences, allow for tail recursion etc.
No if

Avoid using if statements where possible. As Samir said

* "if" is just a special case of pattern matching anyway

Name everything

We should provide named types for primitives including tuples and we should avoid anoymous functions and lambdas.
Use intermediate variables

Avoid chaining function calls, extract into intermediate variables.
Don't abbreviate

Let's be fair, we've all seen functional code with functions like f(), we're not in the dark ages people and we can afford to use more descriptive names to help those who come along later to understand the intent of the code.
What's next

Thse are all preliminary ideas that could help people learn and grow their knowledge of functional programming, they are barely 9 hours old as I write this and we have had our first tentative steps in applying these rules to a code kata. The next step is to try Functional Calisthenics in code katas, see what works, what doesn't are there other rules that would help produce better functional programmers. The discussion is just beginning.


#### Joseph Abrahamson • 9 months ago

Some commentary.

* "Side effects at top level" is a very rough rule of thumb, but really what you want is "side effects taint code". In particular, any time code uses a side effect all of it's callers do, too. This also lets us talk about "benign effects" like Haskell's ST monad which is a side effect that can be proven to be pure.

* "Functions only take one argument" doesn't really have anything to so with SRP, it's just a neat trick that (a) simplifies your language quite a lot and (b) enables partial application with ease. But it's really just a trick.

* "No explicit recursion" I feel is kind of a weird or beginner's approach. Often explicit recursion is exactly how you should proceed, but for simple things like recursing through a list... well, we've done that a whole lot and it's nice to recognize a `map` or `fold`. That's the real heart here—recognize common patterns! If a beginner spends too long building explicit recursion they might not take advantage of most languages' ability to abstract over that pattern.

* "Maximum level of abstraction" is a bit more nuanced. Generally, a function should demand as little of its inputs as it can get away with and produce as sophisticated an output as it can. This means that each application is very generally useful! But this rule also has a boatload of caveats.

* "Use infinite sequences" mostly holds in Haskell where the general rule of thumb is that things are often slow because they're not lazy enough. It's ability to apply in strict languages is suspect at best.

* "No if" feels weird to me. If is the natural eliminator of the boolean type. That said, if your language is lazy then if has a better functional form than as a language statement.

* "Name everything" I *highly* disagree with, to be honest. Names are often meaningless in abstract code—we're interested in the composition of functional pipelines. If you spend too much time naming you'll miss the forest for the highly generic trees.

* "Use intermediate variables" has the same advice as "name everything". These just seem *very* "off".

* "Don't abbreviate" also hits the prior 2 points. The general rule of thumb is that the length of a name is proportional to the size of its scope. If you're exporting a function, give it a nice name. If you're writing a one-liner just to feed into a HOF in the next line then `f` is quite likely to be the more appropriate name... if you must name it at all!

Indeed, I feel very strongly that introducing too many names will prevent someone from ever really grokking FP.





## References

* [Functional Programming in Clojure - Tom Oram](http://tomphp.github.io/functional-programming/2015/06/21/functional-calisthenics-in-clojure.html)
* [Ninja Ferret - Introducing functional calisthenics](http://blog.ninjaferret.co.uk/2015/06/05/Introducing-Functional-Calisthenics.html)
* [Coding Dojo: Functional Calisthenics (2016)](http://www.slideshare.net/pkofler/coding-dojo-functional-calisthenics-2016)
* [Object Calisthenics - Jeff Bay](http://www.bennadel.com/resources/uploads/2012/ObjectCalisthenics.pdf)


Thank you.
[@jr0cket](https://twitter.com/jr0cket)

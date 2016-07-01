title: thinking functional with clojure at DevoxxUK 2016
date: 2016-06-08 23:01:30
categories: Clojure
tags:
- clojure
- events

---
{% img img-thumbnail /images/clojure-logo.png %}

Many languages new and old provide a way to write code using functional programming concepts, however learning those concepts can take a little time especially when they are joined with OO concepts in the same language.

As Clojure has a simple syntax, many find it easier to focus on learning the concepts and design of functional programming.  Then either taking those concepts back to other languages or continuing with Clojure.

At DevoxxUK 2015 I have the pleasure of running a workshop where I can help developers understand the core functional concepts, using Clojure (and Spacemacs) as simple tools.

<!-- more -->

# Who is the workshop for?

{% img img-topic https://danielpecos.com/assets/2015/04/02/xkcd-functional-252x300.png %}

Any developer starting to learning functional programing or interested to understand the concepts should join in.  No prior experience of Clojure is required, although you should get even more out of the workshop if you have a little experience with the language.

As its DevoxxUK I'm assuming most people will have a Java background, but this is not a requirement either.


# Workshop Requirements

The requirements for the "Thinking functional" workshop are quite small and setup is relatively simple.  You will need:

* [Java Runtime Environment (JRE)](https://www.java.com/en/) or the [Java Software Development Kit (JDK)](https://www.oracle.com/uk/java/) - version 8 is preferable (7 or 6 should still work)
* [Leiningen.org](http://leiningen.org/) build automation tool - like Maven but without the XML (project configuration is in Clojure too)
* A Clojure aware editor (not essentai, but recommended)
  * [LightTable.com](http://lighttable.com/) is lightweight & simple to use (written in Clojure / Clojurescript)
  * [Spacemacs](http://spacemacs.org/) / [Emacs](https://www.gnu.org/software/emacs/) - a modern classic all powerful editor come operating system
  * [InteliJ idea](https://www.jetbrains.com/idea/) & [Cursive](https://cursive-ide.com/) - a Java IDE that fully supports Clojure development

See my simple [Clojure development environment guide](https://practicalli.github.io/clojure/development-environments/) for details on setting up Java 8, Leiningen & LightTable.

# The workshop topics

![Puur rogramming Functionally by okeef creations](https://d3nulzlctd9uky.cloudfront.net/blog/wp-content/uploads/2012/05/fp1.png)

With plenty of opportunity to try code out for yourself, this workshop will discuss and provide examples of the following functional programming concepts.

* Pure & impure Functions
* Immutability & persistent data structures 
* Higher Order / First Class functions
* Functional composition / chaining functions
* Functors / map / reduce
* Recursion / iteration
* Sequence / List comprehension
* Lazy Evaluation (Ratios)
* Destructuring / pattern matching
* Polymorphism
* Tail recursion
* Managine state change safely

# In Summary

By the end of this workshop you should know much more about Functional Programming, wether you decide to continue with Clojure or take these concepts to another language.

There are plenty of follow-on resources for Clojure & functional programming included in the workshop and all code will be available in the [Practicalli Github organization](https://github.com/practicalli).

Thank you.
[@jr0cket](https://twitter.com/jr0cket)

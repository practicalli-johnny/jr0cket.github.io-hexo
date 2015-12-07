layout: drafts
title: "midje - repl driven clojure development"
date: 2015-08-17 19:18:38
catagories: dev-tools
tags:
- clojure
- midje
- tdd
---

[Midje]() is a TDD library for Clojure that supports top-down ('mockish') TDD, encourages readable tests, provides a smooth migration path from clojure.test, balances abstraction and concreteness, and strives for graciousness.


# Using Midje with your projects


Add the [latest lein-midje](https://clojars.org/lein-midje) plugin to your Leiningen User profile

```
{:user {:plugins [[lein-midje "3.2-RC4"]]}}
```

> Actually this fails, so tried [lein-midje "3.1.3"] which works


Add the latest Midje library to your Clojure project 

```
[midje "1.8-alpha1"]
```

# Create a new project

```
lein new midje project-name
```

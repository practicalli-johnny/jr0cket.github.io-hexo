title: Clojure Namespaces
---

Clojure has some amazing capabilities when it comes to namespaces and how they import their respective libraries, some more documented than others. That said I wanted to get a few examples down that I've learned to:

hopefully help any others who might have some of the same issues I did, and
for my own edification in case I ever need a reference.
require over use
First and foremost whenever importing a clojure library it is typically recommended to leverage the require syntax over the use syntax. The primary reason for this is to avoid unnecessary namespace conflictions when useing an entire library.

For example, if you had the following:

```
(ns foo.bar
  (:use clojure.string))
```

...then you would receive the below error:

```
WARNING: replace already refers to: #'clojure.core/replace in namespace: user, being replaced by: #'clojure.string/replace  
WARNING: reverse already refers to: #'clojure.core/reverse in namespace: user, being replaced by: #'clojure.string/reverse  
```

If, instead we used require as in:

```
(ns foo.bar
  (:require clojure.string))
```

...then the errors disappear. So what exactly happened? Well when we called use we imported every symbol defined in the clojure.string library to our current namespace. Now, the default namespace that Clojure provides already has a plethora of functions (things in the clojure.core library like map and defn), so when we went and added a few more some collided with previous symbol definitions; namely replace and reverse. On the other hand, when calling require it's essentially telling the system to load those symbols, but not into our namespace. So what does this mean? Well lets check out this code:

```
(ns foo.bar
  (:use clojure.string))

(join " " ["My" "simple" "sentence."])

; => "My simple sentence."
```

In this example join is a function within the clojure.string library and we were able to call it without any other isms (shown below) because we imported all of the clojure.string symbols (i.e. functions) into our local namespace. This will not work if we had used require. Lets take a look at how it would be written to work with require.

```
(ns foo.bar
  (:require clojure.string))

(clojure.string/join " " ["My" "simple" "sentence."])

; => "My simple sentence."
```

As you can see in the above example what we did was qualify the namespace where the join function was since we were referencing a symbol outside our current namespace. If we hadn't done that and requireed the clojure.string library we would've received the following error:

CompilerException java.lang.RuntimeException: Unable to resolve symbol: join in this context, compiling:(NO_SOURCE_PATH:1:1)  
Now that some of the basics are out of the way, lets get into the fun namespace things we can do!

Side Note: I'll be using require specifically from here on out. If you're set on using use then I leave it to the reader to modify the examples.

Referring symbols from require
To import symbols from other libraries into your local namespace, like we saw with use, in a one-off manner one can use the keyword :refer. Following along fron the above, using :refer allows us to write code as follows:

```
(ns foo.bar
  (:require [clojure.string :refer [join]]))

(join " " ["My" "simple" "sentence."])
; => "My simple sentence."
```

The most immediate new addition that you likely saw is the syntactic change to the vector surrounding the clojure.string import. This basically allows Clojure to understand the options you want to apply when importing a library. In the above instance we're adding the addition of the :refer key like we talked about.

I typically find myself using :refer for utility functions (like logging) when I'm:

sure that the symbol is highly unlikely to be used by any other library,
when I use the given function all over the project, and
when the function name accurately represents its use.
Side Note: :refer can take a keyword of :all which makes its use exactly like that of use. For example the below two samples of code are equivalent:

```
(ns foo.bar
  (:use clojure.string))

(join " " ["My" "simple" "sentence."])
```

...and...

```
(ns foo.bar
  (:require [clojure.string :refer :all]))

(join " " ["My" "simple" "sentence."])
```

Assigning namespaces as variables
Probably the most used keyword seen, :as allows you to bind the entire namespace of a given library (like clojure.string) to a symbol. This greatly cleans up the code while maintaining namespace references to avoid collisions. Here is how we would reassign the clojure.string library:

```
(ns foo.bar
  (:require [clojure.string :as clj-str]))

(clj-str/join " " ["My" "simple" "sentence."])
```

What we've done is bind the clojure.string library to the symbol clj-str. Now, when referencing clj-str we can execute any functions as if we had typed the entire clojure.string out before it. Concretely, clojure.string/join and clj-str/join are synonymous in the above example. In fact, since the clojure.string library was imported you could still use the full clojure.string/join even though we bound it :as clj-str if your heart truly desired.

## Grouping libraries by prefix
So we've worked a lot with clojure.string, but, let's be honest, when dealing with actual development the number of imports get voluminous. Luckily Clojure has a nice way to handle prefixing such that namespaced imports start to make sense. They remove unnecessary code to be written and help the readability tremendously. Lets start with a simple example where we want to use not only the clojure.string library, but also the clojure.pprint library. That could look something like:

```
(ns foo.bar
  (:require clojure.string
            clojure.pprint))
```

...or we could tighten it up as...

```
(ns foo.bar
  (:require [clojure string
                     pprint]))
```

## Bringing the basics together
To put all of these features into a production environment lets look at the Storm clojure features. As some readers might know, I work heavily with Storm in my day-to-day and can personally say the below example is in some production code at this moment.

```
(ns foo.bar
  (:require [backtype.storm [clojure :refer [defbolt bolt emit-bolt! ack!] :as storm]
                            [testing :refer [with-simulated-time-local-cluster
                                             with-local-cluster
                                             complete-topology
                                             read-tuples]]
                            [config :as conf]]))
```

The above might seem a bit confusing, but all of the fundamentals are there. To walk through it a bit:

We're importing backtype.storm.clojure and binding it to the symbol storm while referring defbolt, bolt, emit-bolt!, and ack! into the local namespace.
We're importing backtype.storm.testing and referring the function with-simulated-time-local-cluster, with-local-cluster, complete-topology, and read-tuples without binding the namespace to a local symbol.

Finally we're importing backtype.storm.config and binding it as the symbol conf without referring any symbols (i.e. functions) into the local namespace.
Thats all for the basics! Lets move into some of the unique namespace features Clojure has.

## Manipulating clojure.core symbols
One of the lovely concepts in Clojure is that you can actually refer, rename, and exclude given core Clojure functions within a namespace through the :refer-clojure keyword. This is very handy when developing a library with symbols that syntactically collide with a clojure.core-bound function. For example, when I was developing clj-template and making the html bindings a few symbols (i.e. map, meta, and time) collided with core functions already provided. So how do we fix that?

Welcome the :rename keyword. It allows one to import clojure.core functions and :rename them to new symbols. As an example, lets look at how we would change the map, meta, and time function bindings:

```
(ns foo.bar
  (:refer-clojure :rename {map clj-map
                           meta clj-meta
                           time clj-time}))
```

Now, if we attempt to reference map at all we'll get the error:

    foo.bar=> map  
    CompilerException java.lang.RuntimeException: Unable to resolve symbol: map in this context, compiling:(NO_SOURCE_PATH:0:0)  

...where clj-map returns:

    foo.bar=> clj-map  
    #<core$map clojure.core$map@49107ba0>


Hurray!

If we just want to remove certain functions from being imported altogether (for instance, map) we can use the :exclude keyword as follows:

```
(ns foo.bar
  (:refer-clojure :exclude [map]))
```

In the reverse sence we can refer in only specific symbols we want with the :only keyword. Lets look at an example where we only refer in the map symbol:

```
(ns foo.bar
  (:refer-clojure :only [map]))
```

## Conclusions
Clojure provides a lot of power with its dependency system and, in and of itself, can be daunting at times. I hope this helps smooth out its, seemingly, rough edges and provide some concise examples to help better grasp the full potential of Clojure namespaces.


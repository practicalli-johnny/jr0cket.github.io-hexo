title: Why use Clojure - The Business Case
---

Notes from:
http://www.paradiso.cc/2013/12/23/why-use-clojure/

I've seen a few posts now regarding why people should start using Clojure, but until recent events, I couldn't exactly place why I thought Clojure should be used over 'X' language. Now, after becoming a daily user of Clojure, I think I can make a good case for it.


## But first, some history...
Traditionally development languages for a product throughout the years were imperative in nature (think C, C++, Java, etc.) and chosen based on their ease of use1, number of available developers for that language, and, likely, its portability into the given customer domain(s). This whole time product development has been going on other languages, functional in nature, were taking off from an academic standpoint (Lisp, Haskell, Scheme, etc.). Unfortunately the market penetration for the latter set of languages never took off in the commercial sector.

Now, and this is purely conjecture, I can only assume that one of the primary reasons functional languages never took hold from a commercial standpoint was from a lack of qualified developers for those languages in the workplace. The comments I've heard from others in the field today are that those languages are too 'hard' or 'difficult' to comprehend and don't have a place in the commercial world. The statement "yeah, I remember 'functional language x' in college, hated it" comes up all too often. In the end I'd chock it up to poor perseption as its ultimate demise2.

## (def Clojure "v1.5.1")
If you aren't familiar with Clojure then lets begin with a ten second elevator pitch...

Clojure is a functional language built on top of the JVM with sound features in concurrent operations and Java interoperability
Business Case No. 1 - Fewer lines of code is a great thing
Every developer has heard the saying that the number of lines of code written is directly proportional to the number of bugs left needing to be solved. If you've been developing for a while then you probably agree, to some extent or another, the above to be true. Although, if you've never been a functional language person, I would venture to guess you haven't experienced it at such a noticable magnitude. With Clojure, as many will attest3, the average code reduction size from, for instance, Java is roughly 10 times4. Nothing speaks better than an example though so lets look at the Fibonacci sequence and how that would be computed in both traditional Java and in Clojure.

In Java5:
```
public class Fibonacci {  
    public static long fib(int n) {
        if (n <= 1) return n;
        else return fib(n-1) + fib(n-2);
    }

    public static void main(String[] args) {
        int N = Integer.parseInt(args[0]);
        for (int i = 1; i <= N; i++)
            System.out.println(i + ": " + fib(i));
    }
}
```

In Clojure6:

```
(def fib-seq
  (take n (lazy-cat [0 1] (map + (rest fib-seq) fib-seq)))
```

Both examples are extremely brief, but still present the brevity and simplicity of Clojure over other imperative languages.

Business Case No. 2 - Invest early for greater payout later
Functional languages, as personal experience above leads me to believe, are inherently more difficult to comprehend, but provide greater benefit over time. As with a RISC versus CISC architecture debate on whether a small number or large number of instructions are better, so too can the debate reach into imperative versus functional programming languages. The core difference being that for architecture debates the developer doesn't need to actively remember such a plethora of commands.

This concept can be burdensome for many newcomers to Clojure. With a total of around 590 unique functions7 in the Clojure core library alone that can be quite daunting when compared to C or Java which only range from around 30 to 50 keywords. If one takes the plunge though, and moves slowly, they will come out the other end of the tunnel with a host of new capabilities allowing them to operate at higher speeds with a more confident pace and with fewer errors.

## Business Case No. 3 - Natural breakdown of tasks
Anyone who has ever tested code knows that constant and concerted efforts are always taken to ensure everyone is working towards that ever-elusive +90% code coverage. This leads to one of the best side effects (no pun intended)8 of working with Clojure.

Functional languages naturally have a tendency to remove state from within their functions and rather, like mathematics, pass their state in (e.g. f(g(x))). This can be an extremely powerful way to express computation, but becomes burdensome to work with when coming from an imperative language.

But, and this is a large but, because functional languages avoid state and mutable data they have a natural tendancy to break down into convenient subtasks. These subtasks can then be tested, evaluated, and promoted into production code much faster than in other languages. As an example here is the validation function I wrote for a project to verify configuration parameters.

```
(defn validate
  "Given a configuration file as a Clojure map, this will validate each value of each key within
  the map. For all values that do not pass validation they will be logged with the default logging
  mechanism and removed from the map."
  [conf-map]
  (loop [conf conf-map, valid-conf {}]
    (if (empty? conf)
      valid-conf
      (let [[k v] (first conf)]
        (if (contains? pred-val-map k)
          (recur (rest conf) (if ((k pred-val-map) v) (merge {k v} valid-conf) valid-conf))
          (do
            (log/warn "Cannot validate key" k "and value" v "; no predicate validation function found")
            (recur (rest conf) valid-conf)))))))
```

For this example you can assume the pred-val-map looks something like:

```
(def pred-val-map
  {:host #(str? %)
   :port #(let [port (Integer. %)]
            (and (>= port 0) (< port 65536)))
   :version (fn [x] 
              (empty? (filter #(not (number? (Integer. %)))
                              (clj-string/split x #"\."))))
   :description #(str? %)})
```

And finally to test my validate function I would merely need to write a few different map structures to ensure each function acted as it should. This can be done quite easily with Midje, but that is covered in detail below.

It begins to clear up as you work with the language more, but I find that people always gravitate towards this style and end up writing more coherent and cohesive code.

## Compatibility
One of Java's major selling points is the Java Virtual Machine (JVM). That small utility grants any and all JVM-based developer the capability to write code and have it run anywhere and on nearly any hardware. That said, Clojure also benefits from this lovely feature, but in reality that only skims the surface of why Clojure and the JVM work so well together.

Java, with its rich history, has become a force to be reckoned with. It would only make sense that if Clojure could leverage any and all Java code then it would only benefit from the years of development cycles that have already been consumed making Java what it is today. Lucky for us this happened and all Clojure converts can rejoice knowing they have the ability to continue calling their favorite Java libraries from within their Clojure code. This is, in my opinion, one of the major selling points of the language and provides a nice segway for traditional Java developers to move into a functional world.

I won't go into great depth on all of the interopability functions Clojure has, but, if the reader is so inclined, I've found this blog post to be of great assistance when needing examples of Java to Clojure and vice versa.

Tool Suite
What makes a language great isn't just its own innate ability, but that of the community surrounding it and, I must say, Clojure has an extremely active following with some very bright individuals. I don't want to go into great detail here as I feel the 'proof is in the pudding'9, but I will share a few of the major tools I use on a daily basis which should help any beginning Clojure developer.

## Build Automation with Leiningen

Much more than other tools
Much nicer to use 

If you've ever looked at a Maven pom.xml and thought "there must be something easier" then you were referring to Leiningen. It is extremely lightweight, has a simple and concise design, and couldn't be easier to work with. Is it perfect? Probably not, but I haven't found anything I couldn't do that I needed to with it. From deploying to remote Nexus repositories (code signing as well) to polyglot codebase uberjars Leiningen does everything I could ask. Here is a simple example defining a project:

```
(defproject sample-project "0.0.1"
  :description "My sample description"
  :plugins [[lein-marginalia "0.7.1"]
            [lein-javadoc "0.1.1"]]
  :javadoc-opts {:package-names ["tecs.ingest"]
                 :output-dir "docs"}
  :resource-paths ["resources/hadoop"]
  :source-paths ["src/clj"]
  :java-source-paths ["src/jvm/"]
  :javac-options ["-target" "1.6" "-source" "1.6" "-Xlint:-options"]
  :dependencies [[org.apache.hadoop/hadoop-core "1.0.3"]
                 [org.apache.accumulo/accumulo-core "1.4.0" :exclusions [org.slf4j/slf4j-log4j12]]
                 [org.apache.commons/commons-lang3 "3.1"]
                 [com.taoensso/timbre "2.7.1"]]
  ;; These dependencies are used to compile against, but not placed in the uberjar
  :profiles {:dev {:dependencies [[org.clojure/clojure "1.4.0"]
                                  [storm "0.8.2"]]}
             :1.5 {:dependencies [[org.clojure/clojure "1.5.1"]]}}
  :aliases {"docs"
            ^{:doc "Generate all documentation and place in the docs/ folder"}
            ["do" "javadoc," "marg"]
            "build"
            ^{:doc "Build a clean project; like 'fresh!', but without the documentation"}
            ["do" "clean," "deps," "javac," "compile," "uberjar"]
            "fresh!"
            ^{:doc "Pull dependencies, clean the project, build, jar, and generate documentation"}
            ["do" "clean," "deps," "javac," "compile," "uberjar," "docs"]}
  :aot :all)
```

This might seem complex, but in that project I'm also leveraging two plugins which will allow me to generate all the documentation on a codebase which uses both Clojure and Java. Long story short, there's a lot of power packed into that little application.

## Modern dev tool - Light Table
Up until I found Light Table and started working heavily in Clojure my IDE of choice was Emacs (if you can even call it an IDE). I found other IDE's much too bulky, providing myriad features I never used, unstable, or attempting to do too much at once. I am, and always will be, a minimalist and only want what I need to get the job done. That said, the permanent switch to Light Table became apparent after testing it out for a few days and stumbling on the 'InstaREPL' feature. Given Clojure can run in a REPL there is a certain nicety that comes with having this function at your fingertips right next to your code. My typical development time for any activity went down (roughly) 30% because I was able to actively diagnose as I was working. Once I noticed this I knew I'd be working with Light Table full time.

I don't want everyone to think that's the only good function provided though. There are loads of other capabilities packed into that application that I'm continuing to discover and I leave it as a test for the reader to download and give Light Table a try for yourself.

## Testing with Midje
Testing has always been a necessary part of software development, but in my own personal experience testing has never felt quite right. Enter Midje - a beautiful and idomatic way to assert facts about the code you've produced and then evaluate those facts to ensure correctness. If anyone has ever taken a Programming Languages course that sentence should speak volumes.

Here is a simple example taken from the Midje website which walks through evaluating the split function built into Clojure.

```
(fact "`split` splits strings on regular expressions and returns a vector"
  (str/split "a/b/c" #"/") => ["a" "b" "c"]
  (str/split "" #"irrelevant") => [""]
  (str/split "no regexp matches" #"a+\s+[ab]") => ["no regexp matches"])
```

As you can see from the above example Midje helps to further alleviate the testing woes many face by providing a convenient and intuitive way to assert facts that others can readily understand.

## Marginalia
Marginalia has become my de-facto documentation tool. Given the plethora of doc-string capabilities already built into Clojure it is extremely convenient to provide, as nothing more, a Leiningen plugin to leverage the comments which are likely already spattered throughout and offer them up as a beautifully intuitive .html document.

## Clojure Toolbox
The above are only a few of the many tools and libraries available to Clojure. For everything else there's the Clojure Toolbox, a site constantly updated with new and exciting Clojure capabilities categorized by their primary focus (i.e. logging, databases, NLP, machine learning, etc.). Before rolling my own anything I check here first.

## Closing Thoughts
For me Clojure is a gem of language to work with. It has had a net-positive effect on my output at work as well as the mental aspects of my overall work life. Every day I'm more excited to tackle new problem spaces or architect the next application and, to this end, I've seen noticable improvements to my code; in brevity, time to completion, readability, and less erroneous. To conclude I hope I've inspired everyone to take away these two points...

Think about your individual preconcieved notions regarding functional languages and determine if what is there is honest truth or bias from a previous opinion. I'm not trying to convert the world into Clojure experts, but to present facts so that others can see a different point of view regarding functional languages.
Take a moment out of the day and give Clojure a try. It won't hurt and, if you like it, then the community as a whole will only prosper. If you aren't a fan then you have experience and fact to present the next time someone asks you about functional languages.
If you have any questions or comments feel free to email me at brennon@paradiso.cc.

Thanks for reading, until next time!

## References
1 - I use the words 'ease of use' in a relative sense here as that definition is opinionated by the given developer(s) at the time. 
2 - Some agreement with this train of thought; [Why do Java programmers love Scala and shy away from Clojure?](http://stackoverflow.com/a/3346834) 
3 - [One Night With Clojure Makes a Scala Guy Humble](http://agile.dzone.com/news/one-night-clojure-makes-scala)
4 - [Java to clojure rewrite](http://stackoverflow.com/questions/5232654/java-to-clojure-rewrite) 
5 - Shortest fibonacci sequence I could find written in Java; [Princeton Fibonacci Sequence](http://introcs.cs.princeton.edu/java/23recursion/Fibonacci.java.html)
6 - Roughly similar to [this example](http://en.wikibooks.org/wiki/Clojure_Programming/Examples/Lazy_Fibonacci#Recursive_Version) 
7 - Roughly [how many functions are in the Clojure core libraries?](http://stackoverflow.com/questions/17524906/roughly-how-many-functions-are-in-the-clojure-core-libraries)
8 - If you laughed at that then you're already 'in the know' with functional languages. 
9 - Etymology of ["the proof is in the pudding"](http://en.wiktionary.org/wiki/the_proof_of_the_pudding_is_in_the_eating).


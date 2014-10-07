title: clojure-kickstart-workshop
date: 2014-08-19 23:31:08
---

{% img img-topic /images/clojure-logo.png %}

# 01 Clojure Overview - basic characteristics, why I love the language 

Clojure is a general purpose programming language, designed with thought and care to be a modern version of LISP.  Clojure code runs on either the Java Virtual Machine (JVM) or as ClojureScript on a JavaScript runtime (eg. Google V8).

Clojure has a small syntax that is easy to learn.  

Clojure has built in immutalbe data structures and encorages a stateless approach (pure) to functional programming, providing a simple syntax for using transactional memory for all state changes.  This stateless approach makes Clojure ideal for highly scalable applications through parallelisation.  Concurrency and managing threading of your application is no longer the burdon of the developer or a source of major debugging efforts.

Clojure builds on 20 years of virtual machine design via the JVM with all Clojure code being compiled to Java bytecode and run on the JVM.  Calling any of the thousands of Java Libraries (Oracle or community based) is also trivial in Clojure and often simpler to code than from within Java itself due to the elegance of the Clojure syntax.

Clojure is easy to set up and use in your projects as it is packages as a Java Library.  Clojure also has a very powerful build automation tool called Leiningen (the killer of Ants) which manages the creation, dependencies, build and deployment of your Clojure apps.

# Clojure Kickstart topics

* Leiningen - the way to use Clojure
* First Clojure Project - creating projects with leiningen, using templates, basic dependencies
Open command line and type 

    lein new hackference-project

> tour of the project structure

> tour of the project.clj file

> src and test structures - just like java|c#, etc

> talk briefly about different templates

    lein new heroku clojure-on-heroku

    lein help new 

* Exploring Clojure with the REPL - running a basic repl with Leiningen 

From the command line 

    lein repl



* Learning the Clojure Syntax - using the repl, prefix notation, defining functions & data structures, lots of one liners 

> adding documentation to a function then calling the docs on that function to show the dynamic nature of Clojure - its always compiling 

* Understanding the basic design paragims of Clojure
* Clojure Tooling (LightTable, NightCode, Emacs, IDE's) - seperate guide for LightTable & Emacs - just reference other tools
* Creating a basic Clojure App - simple app with CLI output
* Creating a Clojure library - taking some of the functionality out of the above app and putting it into a library, discuss component nature of clojure
* Exploring Clojure core - more common functions from the clojure core libray, 4Clojure 
* Using Java Libraries with Clojure
* Using Clojars
* Creating your own Clojure packages
* Modifying state safely - re-emphasis importance of statelessness, show how to change state safely in Clojure - atoms, etc.


* Creating leiningen templates
* Packaging libraries for Maven Central & Clojars
* Leiningen - more than just the basics - nexus repos, profiles, 


# Clojure WebApp development with Luminus 

> To be put into a seperate Workshop

* Why Clojure for Web App dev - data in, process it, data out... Clojure exceles at this in parallel
* Why Luminus
* Alternatives to Luminus - Pedestal, WebNior (depreciated project), roll your own (worth doing when you have more time to invest)
* First Luminus projects
* Luminus design approach 
* Understanding routes 
* asyncronous web Development
* working with bootstrap / foundation frameworks - repsonsive design for UI
* Defining your own Leiningen templates for Luminus
* Security / access management
* Identiy management with OAuth and Twiter API's etc
* Reactive design
* Attaching a REPL - interactive development

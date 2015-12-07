title: "Speclj - behaviour driven development for Clojure"
categories: dev-tools
tags:
- clojure
- speclj
---

Speclj is a library for Clojure supporting [Behaviour Driven Development] (BDD), an extension of Test Driven Development (TDD) and Acceptance testing.  Speclj helps you design the behaviour of your code and connect it to an automated testing framework.  Speclj is not about testing, except that it by concequence tests your assumptions and show you where you have a broken contract between your specifications and what your code actually does.

> write a better intro...

# Creating a project with Speclj

There is a Leiningen template for any new projects you want to create with Speclj

```
lein new specl project-name
```

Here is an example of the project structure created by the speclj template, for a project called devmeet

![Speclj leiningen template project structure](/images/clojure-speclj-new-project-tree.png)

> To add Speclj to an existing project, include [speclj "3.3.1"] to the project dependencies.  The project must be running Clojure 1.7 or greater.

Speclj is added to the Clojure project as a :dev dependency and a leiningen plugin as follows:

![Speclj project.clj](/images/clojure-speclj-new-project-configuration.png)

You should notice that the `:test-paths` directive is using "spec" as Speclj used `project-name/spec` to contain its specifications.  If you also used [clojure.test] or [midge], then the Speclj files are nicely kept separate.


title: Is there a final programming language?
date: 2011-07-14 16:25:00
categories: events
tags: 
- clojure
---

According to  @UncleBobMartin [the last programming language ever created was C](http://skillsmatter.com/podcast/agile-testing/bobs-last-language), back in the days before I was just a twinkle in the milkmans eye.  All the "new" languages such as Java, Scala, Clojure, C#, F#, etc are rehashes of existing ones.

<!-- more -->

Its also been the case that every "paradigm shift" has been reductive - something has been taken away from the developer.  This is at its most obvious when you consider that virtual machines (JVM / CLR) have taken away code that would be written for memory management.  OO took away pointers to functions, functional took away a lot of freedom in variable assignment (immutable state)  and goto was taken away a long time ago (although its back in F#)


So there arent any new languages since the C language and paradigms have not given anything new for a long time.  Bob asks, if there was just one language that everyone used, [what would it look like](http://cleancoder.posterous.com/the-last-programming-language)?  

There is [no shortage of ideas](http://tlpl.org/index.php?title=Uncle_Bob%27s_last_programming_language "Uncle_Bob%27s_last_programming_language")... 

There is one interesting aspect to a programming language - [homoiconicty](http://en.wikipedia.org/wiki/Homoiconicity). This gives the possibility to write code within your code, constructing complex "fractal" algorithms that could build themselves.  A great modern example of this is the Clojure langauge. Clojure is a very small language, syntactically speaking. “The code is the data, the data is the code”.  It is a functional language that is geared to create complex agorithms working on simple data sets and can allow side-effects through atomic-like software transactional memory. Whether Clojure is the language that attracts a world of developers or a new language evolves from these ideas only time will tell.

Something has been changing in software development though!  Its the people!  Its the practices!  Its the physics!

# The people

There is a much more diverse set of people in the software development industry today compared with 4 decades ago, such as UX designers who create software that is as much a work of art as a service to the user.  Development is becoming more social, not just with people sharing their code (as thats not new, it just a lot more widespread) but also people working together on global projects and getting involved in their local communities.

# The practices

Almost everyone says they are doing agile or trying to become more agile and there has been a major shift (back) to test driven development.  Many teams are adopting frameworks such as Scrum or kanban to help understand how to get work done effectively, thinking as much about how a software team works as they do about the design and quality of the code that needs to be shipped.

# The physics

Until we can get electrons to break the speed of light (tricky) we wont be getting CPUs running any faster, so Moores Law is now being applied to number of cores.  So is multi-core going to produce another language, well it doesnt need to as we already have the likes of Haskel, Erlang, LISP, Scala, Clojure and F#.

So it may seem that C will be the last ever "new" programming language create but as interest grows in other languages the more opportunity for a final programming language to evolve that we all know and is owned by us.  How will the changes in people, practices and physics change how we develop software in future?  Its going to be interesting few decades...

Thank you.
[@jr0cket](https://twitter.com/jr0cket)

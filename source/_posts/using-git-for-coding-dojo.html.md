title: Using Git for a coding dojo
date: 2011-03-31 01:25:00
categories: dev-tools
tags: 
- git
---

{% img img-thumbnail http://git-scm.com/images/logo.png %}

Using Git for a coding dojo gives you a lot of support and should help your experiments and hacking go much smoother.  As its easy to branch different ideas and throw them away, its more likely you will have something still to show at the end of the evening.  Here are some tips on how to use Git at your next coding dojo.

{% blockquote Wikipedia http://en.wikipedia.org/wiki/Dojo %}
A coding dojo is a place where developer gather and practice together.  Dojo is the name for the training halls in Japanese culture use by martial arts students.
{% endblockquote %}

<!-- more -->

# Create a shared git repository

At the start of the coding dojo, create a shared git repository using a service like [Github](http://github.com).  This can be the starting point for everyone and be the place where the code is shared between laptops (should that be required).

1) Get everyone to fork the project

2) Commit changes at suitable intervals during the coding dojo, especially before a refactor.&nbsp; Using lots of small commits will allow people to follow your thinking process and not just the result.

3) Push the code to your forked project.


# Create a local repository 

1) Initialise a local repository 

2) Carry out the coding challenge and do regular commits locally (but no pushes)

3) Create a new remote repository (eg. on Github) and add it a remote reference the local master repository, using the address of your new remote repository.

4)Push your changes to the fork repository to share with your team and others toward the end of the evening.

# An example

{% codeblock lang:bash %}
johnny@Delenn:~$ cd projects/clojure/dojo-ants/

johnny@Delenn:~/projects/clojure/dojo-ants$ ls
project.clj README src test

johnny@Delenn:~/projects/clojure/dojo-ants$ git remote
origin

johnny@Delenn:~/projects/clojure/dojo-ants$ git remote add jr0cket-dojo-ants git@github.com:jr0cket/dojo-ants.git

johnny@Delenn:~/projects/clojure/dojo-ants$ git remote
jr0cket-dojo-ants
origin

johnny@Delenn:~/projects/clojure/dojo-ants$ git status
# On branch master
nothing to commit (working directory clean)

johnny@Delenn:~/projects/clojure/dojo-ants$ ls
project.clj README src test

johnny@Delenn:~/projects/clojure/dojo-ants$ cd src/dojo_ants/

johnny@Delenn:~/projects/clojure/dojo-ants/src/dojo_ants$ less core.clj 

johnny@Delenn:~/projects/clojure/dojo-ants/src/dojo_ants$ git push jr0cket-dojo-ants master
Counting objects: 19, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (5/5), done.
Writing objects: 100% (10/10), 1.46 KiB, done.
Total 10 (delta 0), reused 10 (delta 0)
To git@github.com:jr0cket/dojo-ants.git
&nbsp;&nbsp; f0ac8df..efd6b53&nbsp; master -&gt; master

johnny@Delenn:~/projects/clojure/dojo-ants/src/dojo_ants$

{% endcodeblock %}

Thank you.
[@jr0cket](https://twitter.com/jr0cket)

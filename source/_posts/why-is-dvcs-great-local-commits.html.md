title: Why is DVCS great - Local commits
date: 2012-03-14 21:35:00
categories: dev-tools
tags: 
- git
---

{% img img-thumbnail http://git-scm.com/images/logo.png %}

With a centralised version control system (VCS) like Subversion or CVS you cant start making commits until you have created a repository on the server first.  This slows down the development process and can stop your creativity.  This and other reasons are why I now use a distributed approach using Git.

<!-- more -->

This limitation is a major pain if you are:

*   Off-line
*   Not the administrator
*   Have forgotten how to do it and cant find the docs
*   Are the administrator and its so long ago you don't remember your password
*   Some one else has to approve it<div class="separator" style="clear: both; text-align: center;">

{% img http://4.bp.blogspot.com/-SAdRyX6xiDw/T2ENelQF52I/AAAAAAAAGKs/F1VH7LPiJEk/s1600/git-logo-vertical.png %}

With a distributed version control system (DVCS) you can create a local repository by simply using the command in your project folder:

{% codeblock lang:bash %}
git init 
{% endcodeblock %}

You can then commit changes to that local repository and run comparisons (diffs) for any subsequent changes to your code.  Instantly you can track every file in your project without any convoluted setup.  You also start to capture a detailed history of what you have been up to on the project and if you write good commit messages you know why.

This is a great way to just get on with the coding and letting your creativity flow.

{% img http://4.bp.blogspot.com/-orXHjBQnR_k/T2ENy3lP20I/AAAAAAAAGK0/2MfvKK9-CN0/s1600/source-code-history-visualisation--gource-project-banshee.png %}

Even though you can get on-demand SVN repositories, they still need several minutes to configure - and by the time you have spent setting it all up you have lost your train of thought as to what you were coding.

Using git and a local repository you can create versions from the first line of code (or test) and push your code to a shared space when there is something worth sharing.

Even sharing is relatively easy.&nbsp; You can create a git archive file of your code with all the version history and email it.&nbsp; More likely is you create a new repository on your GitHub account and add this repository as a remote repository (called origin by default) to your local repository.&nbsp; You can then push your changes to the on-line repo for the world to enjoy.

This is just one reason I like Git, Mercurial and Bazaar over Subversion and CVS.

P.s. The visual picture of the DVCS history is from a great little tool called [gource](http://code.google.com/p/gource/), check it out.

Thank you.
[@jr0cket](https://twitter.com/jr0cket)

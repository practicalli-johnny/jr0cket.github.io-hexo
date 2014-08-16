title: Git submodules pros and cons
date: 2014-05-26 15:14:42
categories: dev-tools
tags: 
- git
---

{% img img-thumbnail /images/git-logo.png %}

Git is the version control system of choice by most developers, however when it comes to Git Submodules there is some contention as to their value.  I have used them successfully and when you understand where they fit in you can use them to benefit your own projects too.

I'll explain what Git Submodules as well as why some developers are using them and some developers warn you not to.

<!-- more -->

# Git Submodules Overview

{% img img-topic /images/git-submodules-abstract.png %}

A submodule appears to be just a subdirectory of another git repository.  Actually its a full and seperate git repository itself with its own commit history. 

Submodules are not clones or branches of a single repository and I would advise against merging submodules into the main repository.

You can have many submodules within a git repository and even have submodules in a submodule.

Submodules are useful if you have a code or content in one git repository that you want to use with several other git managed projects, yet you still want to keep the change history seperate.  For example, you may be using a library that is under active development and you need to develop you code along with any changes.

Git Submodules allow you to share two or more repositories as though they were one.  Each repository maintains its own seperate change history and submodules are updated independently of the main repository.  When you clone or pull a repository with a submodule, the repository has a link to where to get the submodle code from.


# My blog: A simple example of Git Submodules

{% img img-topic /images/hexo-submodules-theme-devguides.png %}

I use Hexo.io, a static site generator, to create this blog you are reading.  I create all my content in markdown and push it to a github repository as a backup.  The generated site is also deployed as a Github Pages site.

I started using a Git Submodule with my project as I wanted to make significant changes to the default theme that Hexo uses.  However, I didnt want to add the theme or my changes to the repository I am managing all my content, as I dont want to tie the content to a particular platform.

So by forking the Hexo defalut theme into a seperate repository, I can then add the theme repository as a submodule of my content repository.  I can create a history of changes to the theme and roll back if there are bugs without having to worry about dropping content changes.

I also have an existing repository for a series of developer guides I created, which I can also add as a sub-module and still keep that repository seperate for those who wish to only work with my guides (and not my full content).  


## Prezto: A bigger example of submodules in actions

I use a project calle Prezto which provides a great setup for using Zsh.  The Prezto project pulls in several other projects, each of which configures specific features of Zsh.  Rather than pull all the code into one repository, submodules means that updates from the other projects are easily incorporated into the main Prezto project.


# Git Submodules usage 

To start using git submodules you first need a Git repository, this can be a new repository or an existing one.  Lets call this the _main repository_.

In the root of the main repository, you add a submodule using the `git submodule add` command as follows:

{% codeblock lang:bash %}
git submodule  add -b <branch> --name <name>  <repository>

git submodule add <repository-url> <sub-directory-name>

{% endcodeblock %}

In the man repository you can now see a directory called ... [TODO: Is the directory named after <name> ?]


{% codeblock lang:bash %}
git submodule [--quiet] status [--cached] [--recursive] [--] [<path>...]
{% endcodeblock %}

{% codeblock lang:bash %}
git submodule [--quiet] init [--] [<path>...]
{% endcodeblock %}

{% codeblock lang:bash %}
git submodule [--quiet] update [--init] [--remote] [-N|--no-fetch]
{% endcodeblock %}

{% codeblock lang:bash %}
git submodule [--quiet] summary [--cached|--files] [(-n|--summary-limit) <n>]
{% endcodeblock %}

{% codeblock lang:bash %}
git submodule [--quiet] sync [--] [<path>...]
{% endcodeblock %}

{% codeblock lang:bash %}
git submodule [--quiet] foreach [--recursive] <command>
{% endcodeblock %}


To see the full list of options, please read the [Git Submodules onlne man pages](http://git-scm.com/docs/git-submodule).

# Reasons not to use Git Submodules

Git Submodules add complexity to your version control system and you should ensure using Submodules is more of a benefit than that complexity.  If you ever plan on merging submodules into the main repository, this is possible but its probably better to not use submodules in the first place.


# In Summary 

Git Submodules are a great way to distribute several repositories all as one.  Each Submodule should be treated as a completely seperate repository to get the most sence out of using Git Submodules.  Take the time to learn how to use Submodules and you will find them easy to use and very helpful in the right situations.

* [Git-scm: Git tools - submodules](http://git-scm.com/book/en/Git-Tools-Submodules)
* [Git-scm: Git Submodules man page](http://git-scm.com/docs/git-submodule)
* [Atlassian: Git Submodule workflow tips](http://blogs.atlassian.com/2013/03/git-submodules-workflows-tips/)
* [Git Submodules onlne man pages](http://git-scm.com/docs/git-submodule)

Thank you.
[@jr0cket](https://twitter.com/jr0cket)

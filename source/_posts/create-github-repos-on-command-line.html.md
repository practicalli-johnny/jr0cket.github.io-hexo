title: Create Github repos on the command line with Hub
date: 2013-02-17 16:54:00
categories: dev-tools
tags: 
- github
- hub
---

{% img img-thumbnail http://1.bp.blogspot.com/-qlVcL6zWbjY/TzFMw8PPiGI/AAAAAAAAEbs/-Ozv0X_6mrQ/s1600/github-logo.png %}

Its easy to create a new repository on [Github](https://github.com/) website and then use your git tool or command line to clone it or add that remote repository to your project on your development machine. It would be even easier if you could just do it all from the command line with one command. Well, if you install **[Hub](http://defunkt.io/hub/)** then you can!

<!-- more -->

# Installing Hub

Its easy to install **[hub](http://defunkt.io/hub/)** as its essentially a compiled Ruby script that used your git client to do a lot of the work for it.  If you are using [homebrew](http://mxcl.github.com/homebrew/) on Mac OSX then you can run:

    brew install hub

I havent got round to using homebrew yet, so I just installed hub in my home binaries directory:

    curl http://defunkt.io/hub/standalone -sLo ~/bin/hub

Then I just make hub executable and I am good to go

{% img img-code http://2.bp.blogspot.com/--PmUXufBddE/USEGAdGkGhI/AAAAAAAAJD8/HgWOMkVd8Bg/s1600/github-hub-install.png %}

I could alias hub as the git command as suggested by the hub website, however I want to see the advantages of hub before I fully commit to it. 

# Creating a [Github](https://github.com/) repo without using the website 

In this example I am putting my configuration files onto [Github](https://github.com/) (because after I installed rvm it started rewriting things) so I can manage them better and share them with others.

As usual, I start by creating a local repository for my project files.  This case I am in the home directory. 

{% img img-topic http://2.bp.blogspot.com/-GNsUIzUKsxU/USEE-qL762I/AAAAAAAAJC8/3G-sAxlLhJ4/s1600/github-hub-git-init.png %}

To start with I am just going to add my global git configuration files to the repository.&nbsp; I'll add more later.

{% img img-code http://2.bp.blogspot.com/-neIzVzzUoJg/USEE-q3dtsI/AAAAAAAAJDI/-xASTudbyfg/s1600/github-hub-add-git-global-files.png %}

Using `git status` I can see I have the desired files ready to be committed.  So lets commit them to my local repository with a suitably clear message.

{% img img-code http://1.bp.blogspot.com/--6TpvMsdlMc/USEE-jQi2KI/AAAAAAAAJDM/ffpK4A_I67c/s1600/github-hub-commit-git-global-files.png %} 

Now my git global configuration files are committed locally, so if they change I will be able to compare then to what is in git.

So far I haven't needed to use Hub, but now I want to share these configuration files via [Github](https://github.com/).&nbsp; I could go onto the website and then come back to the command line and add a remote for the [Github](https://github.com/) repository I just added.&nbsp; Using hub, I can just stay in the command line.

Using hub create command I can create a repository on [Github](https://github.com/), specifying the name of the repository and using the -d option I can also include a description 

{% img img-code http://1.bp.blogspot.com/-f1QQzjVV6Jw/USEFALeFKkI/AAAAAAAAJDY/JKx8RdRgDJw/s1600/github-use-hub-to-create-repo-from-local.png %} 

A repository on [Github](https://github.com/) has been created and the remote address was automatically added to my local git project. Yay!

To make absolutely sure just this first time, I have a quick look on the [Github](https://github.com/) website and sure enough there is my new repository.

{% img img-code http://1.bp.blogspot.com/-BPYXNYU2cRs/USEFAFe9VsI/AAAAAAAAJDo/OQ7jVN9HoYE/s1600/github-hub-github-repo-created-on-website.png %} 

Okay, so now I have a shiny new repo on github, its time to push my changes to it from my local repository.&nbsp; Again, we are back to just using git commands.

{% img img-code http://4.bp.blogspot.com/-u0yQgPNi2Yw/USEFAaUo7KI/AAAAAAAAJDg/o_NgrFROnB8/s1600/github-hub-push-git-global-files.png %} 

To check everything is up to date on both the local and remote repositories, I do a quick git log and see (thanks to [my git log customisations](http://blog.jr0cket.co.uk/2013/01/git-log-makes-multiple-repos-easier-to.html)) that the remote repository (origin/master) is at the same commit version as my local repository (master).

{% img img-code http://3.bp.blogspot.com/-hCvA5-QYM-U/USEE_Ufk1rI/AAAAAAAAJDE/Pku_XLfEXpI/s1600/github-hub-git-lg.png %}

# Summary of Hub
There is a lot more to hub that I will try out, but the most immediate use is to be able to create a [Github](https://github.com/) repository without having to switch from the command line.

Thank you.
[@jr0cket](https://twitter.com/jr0cket)


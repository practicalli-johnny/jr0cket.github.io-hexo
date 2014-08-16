title: Github Tip - using SSH for secure transfer
date: 2012-07-02 17:30:00
categories: dev-tools
tags: 
- github
---
{% img img-thumbnail http://3.bp.blogspot.com/-gSyd39LDMRk/TzpVnaZ7ELI/AAAAAAAAEfg/9w1iB-mn5ZM/s1600/github-socialcoding-logo.png %}

Using [Github](https://github.com/) helps me share my code easily.  In a public repository anyone can view code via the Github website.  If you want to work with the code then you can use `git clone` to copy the remote repository to your development machine.  The easiest way to clone the repository is to use its public http address.

However, if you want to push changes back to a remote repository, then you need to use https or Secure Shell (SSH).  As you have to enter your Github username and password each time you do a pull or push, its much simpler to use the SSH protocol `git@github.com:/_username_/_repository_`, especially once you have to [set up a public key for a secure shell (SSH) connection to Github](http://help.github.com/linux-set-up-git/).

<!-- more -->

#  The Scenario

I create a new repository for my [emacs-clojure-kickstart](https://github.com/jr0cket/Emacs-clojure-kickstart) project and then run the git command to clone the remote repository to my local machine:

    git clone https://github.com/jr0cket/Emacs-clojure-kickstart

The remote repository is set to use what ever protocol I specify when cloning, so in this case the remote will be contacted using https.  If I want to push changes then I have to remember my github password and type it into the command line (or add it to my github client configuration).

{% img img-code http://2.bp.blogspot.com/-vIpCWBThzsw/T8ZKPxPTC8I/AAAAAAAAIHU/di86sKgUYA8/s1600/public-private-keys.jpg %}

If I use the `git@github.com...` address of my github repository, then I can push changes and the git client will authenticate using my SSH public key.

    git clone git@github.com:jr0cket/Emacs-clojure-kickstart.git

# Changing the remote

{% img img-code http://4.bp.blogspot.com/-ZczhV0bmNHU/T8ZKxBzj_KI/AAAAAAAAIHc/24xsoWMph3c/s1600/dvcs-centr-decentr.png %} 

So what if I come back to a project after a few days and I have forgotten how it was set up.  How do I see what protocol I am using and how do I change it if its wrong.

Use the command git remote to see what protocol is set up, the -v option gives you the URL as without it you just get the names of the remote repositories.

    git remote -v

If you need to change the remote address, then use `git remote set-url new-url`.  So assuming I have set up the remote to use http and I want to change it to git, I would use the following command:

    git remote set-url git@github.com:jr0cket/Emacs-clojure-kickstart.git

Now I can commit and push changes to the remote server without having to enter my password each time, saving my brain for the coding challenge at hand.

See the post on [password protecting your SSH key](http://jr0cket.co.uk/2012/12/password-protected-ssh-key-for-github.html). 

Thank you.
[@jr0cket](https://twitter.com/jr0cket)

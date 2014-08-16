title: Getting to grips with Git - understanding the Git & Github workflow
date: 2013-08-01 11:09:00
categories: dev-tools
tags: 
- git
- github
---
{% img img-thumbnail http://git-scm.com/images/logo.png %}

Learning to use Git to version your development projects can seem a little strange at first, although once you have a few basics it quickly becomes a natural and fast tool to use.

Here are some of the basics of the Git and Github workflow in word and pictures, created from my mission to teach the world (starting with London) to use Git effectively. &nbsp;If you just want an overview of the basic commands, see my [Git Quickstart Guide](http://jr0cket.github.io/developer-guides/git-quickstart-guide.pdf).

<!-- more -->

# Understanding the basic Git workflow

Git has several stages in the basic workflow:

`Working copy`: the project source code and configurations

`Staging`: add the changes that you want to make a part of the next commit

`Local repository`: the full history of your projects as a series of commits, contained within a folder called `.git` in the root folder of your project.

# Why have a staging area?

The staging area allows you a little more room to consider what the next commit should contain. &nbsp;Its much simpler to change your mind about what will go into the commit by un-staging changes. &nbsp;You also do not have to be concerned about re-writing commit history.

Once you have made a commit, then you should avoid making changes to that commit. &nbsp;Its usually better to fix anything in another commit than to change the first one. 

Once you share a commit with others, eg. via Github or CI server, then you should consult with everyone concerned before making a change to a commit.

# A Git and Github workflow

You can version changes for your project to your local repository as often as you need without conflict as you are the only collaborator. &nbsp;This also means you can work off-line too.

When you want to collaborate on projects you can set up a shared repository that you work on as a team, pushing the commits you made in your local repository to the shared repository.

The most well known example of shared repositories is Github.

{% img img-code http://1.bp.blogspot.com/-n8gwrM5Bf04/UfosDLuuDUI/AAAAAAAAKwg/2aE3V0NDk-g/s1600/git-and-github-workflow.png %}

In the example, John has started work on a project on his laptop and created a local repository using the command `git init`.

John then stages changes using `git add filename` or `git add .` if he wants to add everything.  When John is happy with the changes he has staged and has though of a good commit message, then he creates a new commit with the command `git commit -m "meaningful commit message"`.

John now wants to share code with others, so visits the [Github.com](https://github.com) website and creates a new repository (having first created an account and added his public key to his Github account).

John then tells his local repository about the new Github repository using the command `git remote add remote-alias-name github-repo-url` - where `remote-alias-name` is an alias used to refer to the remote repo and `git-repo-url` is the web address of the Github repository as stated on its github page.

John can then push his changes contained within the local repository to the Github repository using the command `git push remote branch` - where `remote` is the alias for the github repository URL and `branch` is `master` as no other branches have been created at this point. 

## Collaborating via Github

Carlos sees this new repository created by John on Github and decides to get a copy by using the command `git clone remote-repo-url` - where `remote-repo-url` is the web address of the Github repository as stated on its github page.

By cloning the Github repository made by John, Carlos has a new local repository and can see the full history of commits. &nbsp;Carlos can edit the working copy as well as stage and commit his own changes to this new repository. &nbsp;Carlos cannot push changes back to the repository on Github though, so if he did git push it would fail. &nbsp;To update the github repository, John would need to add Carlos as a contributor first.

Sam has also seen the Github repository that John created and rather than take a copy using git clone, she has used the Github website to create a fork. &nbsp;A fork is an exact copy of a Github repository, in this case Sam now has an exact copy of Johns repo but under her Github account and fully accessible by her.

Sam gets a copy of her forked repo on her laptop by using the command `git clone remote-repo-url`. 

Now Sam can edit the code in her working copy and commit those changes to her local repository.  She can also push those committed changes to her forked repository on Github.

If Sam wants to share her new commits with John, then from the web page of her forked Github repository she can [create a pull request](https://help.github.com/articles/using-pull-requests). &nbsp;This sends a message to John to let him know that there are changes in the forked repository that he may want to pull into his Github repository.

Should John accept the pull request made by Sam, then he will also need to update his local repository using the command `git pull remote branch`

Once you are sharing changes thorugh remote repositories, you need to make sure you keep your local repositories up to date with other peoples changes that are pulled into those remote repositories, otherwise it may prevent you from pushing your changes...

# In Summary

Using Git and Github may feel a little strange at first, but once you have some practice and if you keep your workflow simple then using Git will become very natural and fast.

Thank you.
[@jr0cket](https://twitter.com/jr0cket)

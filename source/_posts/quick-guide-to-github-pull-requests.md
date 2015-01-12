title: Quick guide to Github Pull Requests
date: 2014-11-29 07:02:05
categories: coding
tags:
- git 
- github 
---

{% img img-topic /images/24-pull-requests-of-xmas.png %}

  This holiday season give the gift of code... or anything else no matter how small to help out your favorite open source project.  By joining the [24 pull requests website](http://24pullrequests.com/) with your Github account, you can challenge yourself to contribute to 24 projects through December.
  
  Here is a quick guide to creating pull requests on Github.
<!-- more -->

# Contribute via a Github pull request

  Find a project you want to contribute to on Github.  On the top right of its page, press the fork button to create your own complete copy of the project in your own account.  This allows you to add changes (commits) to your own fork, which you then share back to the original project. 

![Fork a project on Github](/images/github-pull-request-fork-gitbookio-plugin-quizzes.png)
  
  Take a copy of your fork using the `git clone` command:

    git clone git@github.com:jr0cket/plugin-quizzes.git
 
![Clone your fork](/images/github-pull-request-clone-gitbookio-plugin-quizzes.png)

   Its very useful to create a branch for the change you are going to make.  If there are project updates while you are creating your contribution or you just mess up so bad you just want to throw your contribution away, then a seperate branch makes this easy.
   
    git checkout -b doc-plugin-configuration

![Fork a project on Github](/images/github-pull-request-branch-create.png)
    
  Edit the files that make up your contribution and test your changes work before you do a local commit.  Here I am updating the README.md file with some clearer instructions on how to add the plugin to your project. 
  
    git add README.md 
    git commit -m "adding instructions on configuring the plugin"

![Fork a project on Github](/images/github-pull-request-commit-locally.png)

  Now copy your local commit back to your fork of the Github project.  Remember to push the branch you created and not the master branch.
  
    git push origin doc-plugin-configuration

![Fork a project on Github](/images/github-pull-request-push-to-fork.png)

  Once you have pushed your branch to your fork, Github gives you the option to create a pull request.

![Create a Pull Request](/images/github-pull-request-create-pull-request.png)

  When you create the pull request, it uses your commit message as the title of the pull request.  You can also add further information if it helps the project maintainers understand what the change is about and why they should accept it.
  
![Pull Request message](/images/github-pull-request-message-example.png)

  Create the pull request and then wait for the project maintainters to talk a look at your change.  If your change has a large green icon next to it, it means it can easily be merged into the project.
  
![Pull Request submitted](/images/github-pull-request-push-submitted.png)

## Patients is a virtue

  Its now time to wait for the project maintainers to review your pull request.  If they like what they see and its easy to merge into the project then that may happen fairly quickly.  However, as it's their project then it is up to them what they accept.  This is why small contributions are better than large, so you can develop good communication with the project maintainers with the minimum of effort.

## Planing to contribute regularly

  If you want to are going to contribute to a project over time, its a good idea to create your own fork.  Also, once you have cloned your fork, you should also add the original project repository.  
  
    git remote add upstream git://github.com/project/repository-name

  Before you make any change or create a new branch for your change, you should get all the latest updates from the original project.
  
    git pull upstream master

## Updating your own fork 

  If your pull request is accepted then you can pull that commit into your own fork by pulling the changes from the original project and pushing them back to your fork.

    git pull upstream master 

> If you have other changes in the working copy, you can always use `git stash` before you pull in order to keep your work safe.  Once you have done a pull you can use `git stash pop` to restore the changes back to your working copy.


Thank you.
[@jr0cket](https://twitter.com/jr0cket)

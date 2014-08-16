title: London Scala Hackday powered by Heroku
date: 2012-10-30 14:32:00
categories: events
tags: 
- hackday
- heroku
- scala
---

Saturday 27th saw a great hackday thanks to [Robert Rees](https://twitter.com/rrees), The Guardian and members of the [London Scala user group](http://www.meetup.com/london-scala/).  The ambitious challenge was to build an community website where events, conferences, blogs, code repos and  community discussions were all available from one place.

There are several websites out there that do a part of what a community  needs, to this project is trying to help bring all that together in one  place.  So the grand plans include, pulling in content from event sites,  publishing events to sites, register at events with a single touch and  widely distribute your interest and attendance automatically.

Or just have fun hacking on some cool technology and learning something new.

<!-- more -->

# The basic architecture

The hack used the [Play framework](http://www.playframework.org/), a recent development that makes developer lives easy when building web applications.  A project had been started a couple of weeks ago using Play Framework 2.0.3 although as there was a new update, we moved to 2.0.4 during the hackathon.

[Heroku](http://www.heroku.com) has been used as the deployment platform as it makes everything really easy.  You can deploy with a commit to a git repository.  So long as your build file works locally, then you can deploy on Heroku.

As we were using Heroku, we made use of [several addons availalbe](https://addons.heroku.com/), specifically adding [MongoDB](https://addons.heroku.com/mongolab) to the design.  MongoDB would be used to pull in information from sites  that had a limited hit rate.  Mongo could also be used for holding any  adhoc data we wanted to keep around.

# The deployment process

{% img img-topic http://1.bp.blogspot.com/-qlVcL6zWbjY/TzFMw8PPiGI/AAAAAAAAEbs/-Ozv0X_6mrQ/s1600/github-logo.png %}

Andy Hicks, our beloved community leader created a play framework project.  Then set up an heroku account, adding a couple of extra people as collaborators to be responsible for pushing changes to live.

Although we could just deploy directly onto heroku, its useful to [Github](http://www.github.com) as your development repository.

Using Github, you can manage the code base by forking the main repo and submitting change via github pull requests.  This encourages developers to commit often and make smaller changes, essential things if you only have a few hours to get things live.

# Continually deploying
{% img img-topic http://4.bp.blogspot.com/-Gpk2Bz1KOSU/UI_b8kGF5fI/AAAAAAAAIeA/0tjExsTaL6E/s1600/lsug-hackathon-commit-graph-text.png %} 

Even though we were first commiting changes to github, we still pushed the  changes to Heroku regularly.  I would push changes up to Heroku after each pull request had been successfully merged.

If there were multiple pull requests waiting (usually due to fixing a conflicting pull request) then I'd merge all the outstanding requests before pushing to heroku.

The deployment process was essentially myself pulling changes from the github repository to my laptop, then pushing everything to the heroku git repository.

# Keeping up to date

One trick we learnt to make things easier is the `git stash` command.  If you have been working away on your code and realised you  were behind master, you can hide away the changes in your working copy  and git pull from the master without loosing your changes.

When you run the command `git stash pop` then your working copy changes are re-applied and you can resolve any confilcts you have before commiting.

    git stash
    git pull lsugweb master
    git stash pop 
    <resolve any conflicts>

Alternatively, if you are doing more experimentation then a branch was created to work  on which would then be merged and committed into master if it was valuable code.

    git branch branch-name
    <edit you code base>
    git merge branch-name master

# Challenges 

**Git experience**:  
Although git is very popular now, many developers are still learning how to use it effectively, especially when working collaboratively.  

**.gitignore**: 
We had quite a few conflicting pull requests due to the `.gitignore` file.  So to keep things simple we agreed to keep changes to `.gitignore` seperate from code commits.  Likewise with any other non-essential config changes.  Add **.gitignore** to `.gitignore` and just  maintain a managed set of ignore files

**Keep commits small:**:
Its  was so much easier to merge a series of small changes when you are using pull requests, especially when you have someone managing the queue  and can merge those changes quickly.  The bigger the commit, the longer it takes to merge and backs up your pull requests.  Our largest commit affected 73 files and it took several attempts before we could get it to automatically merge.  At least it gave us chance to talk about the  change in more detail.

It was a great hackathon and thanks to everyone that came along, [Robert Rees](https://twitter.com/rrees) for orgaising and The Guardian for hosting us.  Why not get yourself to a hackathon and join in the fun, or even organise your own ?

Thank you.
[@jr0cket](https://twitter.com/jr0cket)

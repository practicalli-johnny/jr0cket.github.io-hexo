title: Continuous Integration with Travis-CI, Scala, Play2 and Heroku
date: 2012-12-11 13:05:00
categories: dev-tools
tags: 
- scala
- ci
---

{% img img-thumbnail http://2.bp.blogspot.com/-kIrzG80xsL4/UMcqsNDxzzI/AAAAAAAAIsU/hKMCeoPdGkk/s1600/lsug-logo.jpeg %}

During the London Scala community hackday at the Guardian, we first put together the [LSug community webapp](http://lsug.org/).  For this we used Play2 framework, MongoDB, Github for pull requests and deployed onto Heroku.

Towards the end of the hackathon, someone suggested we also wired the project up to [Travis-CI](https://travis-ci.org/), although none of us knew much about using it.  As the hackday was all about discovering how to use new stuff, I decided to add Travis-CI and worry about setting it up when we got to it.

# What is Travis-CI ?

{% img img-thumbnail http://2.bp.blogspot.com/-5VmP6LuMgJQ/UMcriwrutXI/AAAAAAAAIsg/9z1McNPoKio/s1600/travis-logo.png %} 

[Travis-CI](https://travis-ci.org/)** is a [continuous integration](http://en.wikipedia.org/wiki/Continuous_integration) service that allows you to run build jobs and tests automatically, straight from Github.  Its ideal for open source projects.

As its on the web then there is no installation required and its really easier to configure.  You simply point Travis-CI to your Github account and you can choose which projects you want Travis-CI to run on.  Travis-CI will scan you public repositories, as well as any Github organisations you are part of.  Its then an easy matter of switching on those repositories you want Travis-CI to monitor (eg. build, run tests, etc.)

# Travis-CI in action

Whilst Travis-CI has been pointed to the the [lsug-dojo/lsug-website repo on github](https://github.com/lsug-dojo/lsug-website/) via my account, no one got round to adding a Travis-CI configuration file.  The down side of this is that those contributors to the lsug-dojo/lsug-website repository received an emailed error message each time something was pushed to the repository or a pull request was accepted.

Not having a working Travis-CI was also noticeable when reviewing pull requests, as Travis-CI talks to Github and lets it know that your projects have failed.  It then up to you wether you still want to merge.

{% img img-code http://3.bp.blogspot.com/-qRhXKVybkpM/UMctV4nRu0I/AAAAAAAAIss/liJmosF0rNk/s1600/travis-ci-pull-requests-caution.png %} 

[Screenshot taken from travis-ci blog </span>](http://about.travis-ci.org/blog/2012-09-04-pull-requests-just-got-even-more-awesome/)

With a quick Google I found an [example travis-ci configuration file for Play 2 framework](https://github.com/gildegoma/travis-ci-ScalaOnPlay-sample/blob/master/.travis.yml).  I just dropped in a new `.travis.yml` file into the lsug-website github repository and that triggered another travis-ci build.  This time the test ran and passed!!

{% img img-code http://4.bp.blogspot.com/-NckYSnj2G8w/UMctWvTZ0bI/AAAAAAAAIsw/5tHd9x3zVbo/s1600/travis-ci-pull-requests-good.png %} 

[Screenshot taken from travis-ci blog](http://about.travis-ci.org/blog/2012-09-04-pull-requests-just-got-even-more-awesome/)

One benefit of using Travis-CI is to encourage the use of tests, it also gives information about the state of the github repository.  This is especially useful when working with pull requests.

This is the first time I have used Travis-CI and it was really easy to configure.  If you have any comments or ideas about this, please share them with the group or myself directly.

Thank you.
[@jr0cket](https://twitter.com/jr0cket)


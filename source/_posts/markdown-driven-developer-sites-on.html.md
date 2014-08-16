title: Markdown driven developer sites on Heroku - easily create an online workshop
date: 2013-01-21 13:58:00
categories: dev-tools
tags: 
- heroku
- markdown
- depreciated
---

{% img img-thumbnail http://2.bp.blogspot.com/-yIBn-HYfxeA/UI_UGVJF6AI/AAAAAAAAIdo/MLPDWYCbX2Q/s1600/heroku-logo-light-300x100.png %} 

[Heroku](http://www.heroku.com/) is a great platform to deploy your web apps, in a way that just works  for developers.  What isnt obvious is you can also deploy static sites too.

As Markdown is now common way for developers to  create documentation, why not use Heroku to deploy your markdown driven content site.

<!-- more -->

## Collaborating force 

The [Salesforce developer evangelist team](http://developer.salesforce.com/) are doing just this, creating workshops written in markdown.  The workshops are deployed on Heroku and we collaborate via Github.  This is a really effective way to collaborate as we are remote workers and often on our travels. 

## Markdown is simple
{% img img-topic http://2.bp.blogspot.com/-vdbLJDFnR7Q/UPxhMffM05I/AAAAAAAAI8k/1HLAKXNX5jU/s1600/markdown-logo.gif %} 

Markdown is really easy to learn and really easy to read.  Its much better to read in its raw form than most Wiki Markup languages.  If you have a good editor (Emacs & Emacs Live) then reading and writing markdown is a great experience.

Its also pretty easy to convert Markdown to different formats such as HTML and PDF.

I picked up all the markdown syntax from working with Github readme.md files and from writing markdown in Emacs.  SimpleCode.me also has a really good [getting started with markdown guide](http://www.simplecode.me/2011/12/11/getting-started-with-markdown/). 

## Creating the content in markdown

{% img img-topic http://2.bp.blogspot.com/-hiVZZWkLlbg/UPAGL_h-U4I/AAAAAAAAI5Q/J3CzFdhvziw/s1600/emacs-live-docs-themed.png %} 

Any editor can be used two work on the content for the workshops, this is another beauty of markdown.  I recommend Emacs with [Emacs Live setup](http://blog.jr0cket.co.uk/2013/01/emacs-live-great-clojure-developer.html) or you are using MacOSX, then [Mou](http://mouapp.com/) gives you live rendering of you content as you type.

To make the markdown render in HTML and PDF similar to the style used on github, a fairly simple css file is added to the project. 

## Creating your app on Heroku
As Heroku and Github are both going to be used then the projects are versioned with Git.  A git repository is created on Github at the start of a new workshop.  A github  organisation is used to keep al the projects together.  The new Github repository is cloned and development of the content commences.

> As its a static site then there is not much need for a .gitignore file, assuming you have [a ~/.gitignore_global file for any backup files](http://jr0cket.co.uk/2012/12/gitignore-for-clojure-and-emacs-ignore.html) that your editor creates.  

Once the workshop content is good enough to deploy, a new Heroku application is created.  A specific [build pack](https://devcenter.heroku.com/articles/buildpacks) is used to tell Heroku how to assemble and deploy the markdown as a web  application.  This build pack defines how the HTML is generated from  the markdown, based on a css file included in the project.  The whole  app runs on a HTTP server called SimpleHTTPServer, written in Python.

The app is created on Heroku app using the [markdown build pack](https://github.com/jamesward/heroku-buildpack-markdown) created by James Ward.  The command line for this is:

    heroku create workshop-name  --buildpack https://github.com/jamesward/heroku-buildpack-markdown.git

## Telling Heroku how to run your app
A procfile is a simple text  file that tells Heroku what to do with you application when its ready to  run it.  For the markdown site we simply start up a simple HTTP server  which runs on python (we dont need all the bells and whistles of something like Apache).

The `web:` directive at the front tells heroku to create a process that listens to requests from the Internet.  As we are not  specifying a port number, it will pick up the default port to listen on  from the Heroku environment variables.

    web: python -m SimpleHTTPServer $PORT

## Deploying the markdown site
{% img img-topic http://1.bp.blogspot.com/-qlVcL6zWbjY/TzFMw8PPiGI/AAAAAAAAEbs/-Ozv0X_6mrQ/s1600/github-logo.png %} 

As soon as you are ready for your  markdown content to go live, simply push your local repository up to the  Heroku repostiory with the git push command.

    git push

If you have more than one remote repository specified in your git configuration, then all you need to do is specify the specific repository to push to.  By default the heroku create command adds a remote called heroku.

To check what your heroku repository is called you can use the command:

    git remote -v

To push to a remote repository called heroku, use the command:

    git push heroku master


## In summary
It is really easy to create content based on markup. Collaborating on this content is really easy when using Github and deploying this content as a static website is only a git push away with heroku.

Other aspects were are adding to this workshop creation process include:
* create a staging heroku app to allow testing of content once the site has gone live;
* automatically generating a pdf copy of each page every time you deploy a new version.

Thank you.

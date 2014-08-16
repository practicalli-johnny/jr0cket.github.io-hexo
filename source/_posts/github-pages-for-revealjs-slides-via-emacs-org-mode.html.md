title: Github pages for Reveal.js slides created with Emacs Org-mode
date: 2014-01-03 13:34:00
categories: presenting
tags: 
- emacs
- orgmode 
- github
---

{% img img-thumbnail http://1.bp.blogspot.com/-qlVcL6zWbjY/TzFMw8PPiGI/AAAAAAAAEbs/-Ozv0X_6mrQ/s1600/github-logo.png %}

In previous articles I showed how to [setup Emacs Org-reveal & Reveal.js](http://blog.jr0cket.co.uk/2013/09/create-html5-presentations-emacs-revealjs.html) to [generate your own presentations](http://blog.jr0cket.co.uk/2013/10/create-cool-slides--Org-mode-Revealjs.html) from Emacs Org-mode files.  This time I'll show you how to publish those presentations on [Github Pages](http://pages.github.com/) as I have done for [my own presentations](http://jr0cket.github.io/slides).

<!-- more -->

[Github Pages](http://pages.github.com/) are a great place for publishing your [Reveal.js](http://lab.hakim.se/reveal-js/) presentations or any static web content. For existing repositories you simply commit your content to a _gh-pages branch_ or to the _master branch_ of a user or organisation repository.

{% blockquote %}
[Github Pages](http://pages.github.com/) are great for websites that is self-contained, in that there is no reliance on a database or other services running locally.  You can even create great looking pages without any coding by using the Github authoring tool.
{% endblockquote %}

# Existing code repositories

If you already have a repository for your code and want to add web page documentation, then you can simply add a _gh-pages branch_ and commit your web content to that branch.

{% img img-code http://1.bp.blogspot.com/-qlVcL6zWbjY/TzFMw8PPiGI/AAAAAAAAEbs/-Ozv0X_6mrQ/s1600/github-logo.png %}

# Content only repositories

If you only have content then you can use a _user_ or _organisation_ repository.  This is a specifically named repository in the form of `name.github.io` where `name` is the exact name of your Github account or Github organisation you are part of.

In my case I [created a repository](https://github.com/new) named `jr0cket.github.io`, as my Github user account name is jr0cket. 

Once created, you can type in the name of this repository into your browser and it will display any content you have committed into the repository and pushed it to Github.  

Your user or org repository also forms the entry point for other project, so if you have a project called _slides_ with web content in its _gh-pages_ branch, you can see that content using the address: http://jr0cket.github.io/slides

# Separating slide content into their own repository

As I planed to create a number of presentations, I use both an account repository as the home page and created a new repository called slides to host all my presentations. &nbsp;This allows all my presentations to be easily cloned or forked by others easily without getting content that is only relevant to me on my Github pages home page. 

Keeping the presentations all in one repository keeps things simple should I define my own Reveal.js themes or if there are Reveal.js updates.

I added &nbsp;everything to the _gh-pages_ branch (reveal.js, images, org &amp; generated html files). &nbsp;Then I generate the Reveal.js slides locally using org-reveal in Emacs, so I can check they look okay. &nbsp;Once I am happy with the slides I commit the html and .org files to Git and push them up to Github.

# Setting up a Github Pages user account repository

Creating an user repository on Github is just the same as for any other repository, except that the name must match the form name.github.io - where name is exactly the same as you Github user name.

I created a new repository called `jr0cket.github.io`, this has a web address (URL) of [http://jr0cket.github.io](http://jr0cket.github.io/)

I used the Automatic Page Generator from Github to create the site without coding and with a handful of nice templates to choose from. &nbsp;You can of course add your own HTML, CSS &amp; JavaScript if you wish. &nbsp;The Automatic Page Generator is in on the Settings page of your repository, under the Github pages section. &nbsp;This section shows you the repository URL and a button to generate a page for you.

If you are going to use your user or org repository for your slides, then jump to the secion on "Adding Reveal.js to your repository"

# Creating a repository for your Reveal.js slides

If you don't already have a Github repository for your slides (and are not using your user or org repository), go to your account on Github and [create a new repository](https://github.com/new).

    git clone https://github.com/username/repository.git

# Create an orphaned gh-pages branch

Github pages publishes content only from the branch gh-pages (unless you are using a user or org repository). In your local repository, create a new branch called gh-pages. According to Github, the gh-pages branch should be an orphaned branch.

    cd your-local-repository
    git checkout --orphan gh-pages

> An orphaned branch is one that is not connected to another branch, in this case its not attached to master. Technically I don't think gh-pages branch needs to be orphaned to publish your content, especially if there is nothing in the master branch, but this is [the approach that Github recommends](https://help.github.com/articles/creating-project-pages-manually).

Once you have the gh-pages branch you can commit your files to that branch as normal. 

    git add .
    git commit -m "Adding Reveal.js files for presentation"
    git push origin gh-pages

Pushing your Reveal.js slides at this point will not give you the desired results, as we haven't added the Reveal.js files to the repository. &nbsp;So lets do that next.

# Adding Reveal.js to your repository

You need to provide the JavaScript and CSS files from Reveal.js to make your slides display correctly. &nbsp;I copy the following folders from within the reveal.js folder into the root of my slides project

    cd  /path/to/revealjs/css    ~/my-slides
    cd  /path/to/revealjs/js     ~/my-slides
    cd  /path/to/revealjs/lib    ~/my-slides
    cd  /path/to/revealjs/plugin ~/my-slides

You also need to check that the HTML for your web pages references Reveal.js files correctly. &nbsp;The best way to do this is in the configuration for Emacs Org-reveal.

In my Org-reveal setup, I have defined the root for the Reveal.js files in my live-pack `init.el` file as follows:

    (setq org-reveal-root "")

So long at this org-reveal setting is loaded, it shouldn't matter which file you add it to in your Emacs configuration.

The HTML you generate with Org-reveal in Emacs should have references to the Reveal.js includes in the `<head>` section. Here is an example:

    <html lang=”en”>
    <head>
      <meta charset=”utf-8”/>
      <title>(My presentation title)</title>
      <meta name=”author” content=”(John Stevenson)”/>
      <link rel=”stylesheet” href=”./css/reveal.min.css”/>
      <link rel=”stylesheet” href=”./css/theme/jr0cket.css” id=”theme”/>
      <link rel=”stylesheet” href=”./css/print/pdf.css” type=”text/css” media=”print”/>
      <meta name=”description” content=”My presentation title“>
    </head>

# The final push
Then push the Reveal.js files to your Github repository (and any updated to your Org &amp; html files)

    git add .
    git commit -m "Adding Reveal.js files for presentation"
    git push origin gh-pages


# Browsing your Slides

If you added your slides to a user or org repository, then you should be able to browse to http://name.github.io where name is your Github user or org name (eg. http://jr0cket.github.io).

If, like me, you created a seperate repository for all your slides, you can brows them by going to http://name.github.io/repo-name where name is your Github user name and repo-name is the name of the repository you added Reveal.js and your slides to (eg. http://jr0cket.github.io/slides).

Note that you need to add the html filename to the URL to browse your presentation, or as I have done add links to the page on [jr0cket.github.io](http://jr0cket.github.io/slides)

# Using Hub as an alternative way to create your Github pages repository

Hub is a command line tool for working with git repositories and Github.  Hub makes it easy to create and fork repositories on Github without having to visit the Github website.

* Install [**Hub**](http://hub.github.com/)
* Create a folder called `name.github.io` on your laptop, where name is your Github user name or organisation name
* Inside that folder, initialise a git repository - `git init`
* Rename the master branch to gh-pages - `git branch -m gh-pages`
* Use hub to to create the repository on github - `hub create -d "optional description of the repository"`
 -- If you want to specify the repository name using hub, use the command form - `hub create account-name.github.io -d "optional description of the repository"`

* Create and commit your content in the local repository on the gh-branch, then push the gh-pages branch to github `github push -u origin gh-pages`

-- The -u option sets origin to be the default remote repository to and the gh-pages the default branch.  So next time you do a push or pull you dont need to specify the remote repository or branch, you can simply do `git push` and `git pull`

# Example Reveal.js presentations on Github pages

See [my Github page](http://jr0cket.github.io/slides) for my published presentations, created with Emacs Org-mode, Org-reveal and Reveal.js.

Thank you.
[@jr0cket](https://twitter.com/jr0cket)

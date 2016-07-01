title: publishing for developers with Gitbook.io
date: 2016-06-07 22:29:29
categories: gitbook
tags:
- gitbook
- github-pages
---

{% img img-thumbnail /images/gitbook-logo.png %}

The tools for writing books and workshops have become so much easier and open.  Even some enlightened publishing companies are moving with the times and not forcing you to write books in seperate word files.  However, having to manage the expectations of a publisher can make book writing very unattractive.

Self publishing is much more fun and can be done at your own pace, using tools a developer can understand.  Its also much easier to talk to a publisher when the book is mostly done.

I use [GithubIO/gitbook](https://github.com/GitbookIO/gitbook), a node.js project to create my books and workshops.  Gitbook generated a responsive design website as well as ebook formats in pdf, epub, etc.

All the content is written in [markdown](https://guides.github.com/features/mastering-markdown/) and can be managed with [Git](https://git-scm.com/).  There are also a range of [Gitbook.io plugins](https://plugins.gitbook.io) that enhance the readers experience in terms of content style and user interaction.

> You can also distribute your books via the self-publishing platform of [Gitbook.io](https://gitbook.io) where you can sell your books on its marketplace.

## Advantages of Gitbook.io

* Simple to use tools, requiring only node.js to be installed
* Writing content in markdown keeps it human readable as you write it
* 100+ plugsins help you style the book, applying different styles to the range of formats
* Content can be managed in Git and collaboration can be done in services such as Github or Bitbucket
* Website versions can be published on any webserver, Github Pages works well for these.

Lets set up Gitbook.io and go through the content workflow.

<!-- more -->

## Setup Gitbook

Gitbook is a node package so [install the latest version of node.js](https://nodejs.org/), version 4.x and 6.x work with Gitbook.

install GitBook via the nodejs package manager (npm) using the command line:

```
$ sudo npm install gitbook-cli -g
```

`gitbook-cli` is an utility to install and use multiple versions of GitBook on the same system. It will automatically install the required version of GitBook to build a book.

> You should use `sudo` or install gitbook-cli as an administrator, unless you have installed node.js in your personal file space.  The `-g` option makes the gitbook commands global, so you can use them anywhere on the command line.

## Create a new book

To create a new book, simply create two files:

* `README.md` - introdution page to the book
* `SUMMARY.md` - the structure of the book

Then run the Gitbook initialisation command in the directory containing these two files

```
$ gitbook init
```

If you wish to create the book into a new directory, you can do so by running `gitbook init ./directory`


## The book structure 

The `README.md` file should have a description or introduction to the book, written in markdown.  If its a workshop you are writing, its good to state what people will learn and what the prerequisites are.

The `SUMMARY.md` file defines the structure of the book, it too is written in markdown.  Here is a sort example of a `SUMMARY.md` file

```
# Summary

* [Introduction](README.md)
* [How to use the workshop](using-the-workshop/index.md)
    * [Technical Requirements](using-the-workshop/requirements.md)
    * [Code Examples](using-the-workshop/code-examples.md)
* [Overview of Clojure](overview/index.md)
    * [When to use Clojure](overview/purpose.md)
    * [Who uses Clojure](overview/who-uses-clojure.md)
    * [The syntax](overview/syntax.md)
    * [Design](overview/design.md)
    * [Read, Evaluate, Print Loop (REPL)](overview/repl.md)
```

If you add new sections to the `SUMMARY.md` file, then running `gitbook init` again will create the relevant directories and create files including the section tiles.

> Using Spacemacs / Emacs allows you to easily re-order the sections of the book in the summary.md file by usig the `Alt + Up Arrow` or `Alt + Down Arrow`


# Generating the book

You can see what the website version of your book looks like by running the Gitbook server

```
$ gitbook serve
```

Or build the static website using the Gitbook build command and serve it up from whatever webserver you prefer.

```
$ gitbook build
```

# Deploying your book to Github Pages

I typically use Github Pages to serve my content.  Its easy for developers to use, supports custom domains and is where I typically version the content I am writing so its convieninet to have it all in one service.  Github also makes use of a content delivery network (CDN) so serving your book website is incredibly fast.

I havent seen a built-in way or plugin to deploy to Github Pages, so I use a very basic script(this could probably be done better).

```
#!/bin/sh

# Replace the remote Github URL to use this on a different project

# This should be run from the root of the gitbook project
# Delete the previous book build
rm -rf _book

# Trigger a clean and new build
gitbook build .

# Deploy new build
cd _book && git init && git add . && git commit -m "automated commit from gitbook.io" && git branch -m master gh-pages && git remote add practicalli git@github.com:practicalli/clojure.git && git push -f practicalli gh-pages
```

# Wriing your book - Essential Markdown

All the content can be written in [markdown](https://guides.github.com/features/mastering-markdown/), even the book structure. As its markdown, each section and sub-section of the book is human readable and have really minimal notation for style

## Headings

To create headings, use the hash, `#`, character.  A single hash represents the biggest heading, equivalent to a H1 in html.

```
# This is a main H1 style heading
This is the text that goes underneath the headding

## This is a sub heading, equivalent to H2
```

## Links 

The markdow to create hypertext link, a clickable link to another page in the book or external website.

```
[Clickable Text for link](/path/to/linked-page.html)
[Clickable Text for link](http://linked.com/page.html)
```

## Images

The markdown to include an image in your content is:

```
![Image description](/path/to/image.png)
![Image description](http://website.com/image.png)
```

This markdown will include a centred image in your content.  Positioning of the image is managed by the theme and can also be changed in the `styles/website.css` for the website or `styles/pdf` for the pdf version of the book.

> Images can be put in the book filespace and saved in Git along with the other content.  If you have very large images or thousands of images, it may be better to use an onlie image service , eg Amazon Web Services Bucket, especially if that service has a content delivery network (CDN) to provide a consistent download speed for images where ever someone is viewing your book website.

## Source code 

You can highlight short snippet of code inline with the content just by placing a single quote at the start and end of the code.

Or you can highlight a block of code with three consecutive single quotes at the start and end of the code.

# Gitbook Plugins 

There are [over 300 plugins available](https://plugins.gitbook.com/) which help give a better experience in reading the book.

* `toggle-chapters` - collapses all the sub-headings of the book in the website, except for the section you are currently viewing.  Really good for books longer than 10 sections.

* `disqus` - an discussion platform for enabling comments from your audience in your book, in a way thats easy to control.

* `ga` - a simple way to add Google Analytics to your book website.

# Summary

The hardest thing about writing a book should be writing something valuable and engaging, that is hard enough already.  Everthing elese should be trivial to do or you will have more reason to become demotivated.

Using tools like Gitbook.io or [ReadTheDocs](https://readthedocs.org/) can make writing books and technical content much more fun.

Thank you.
[@jr0cket](https://twitter.com/jr0cket)

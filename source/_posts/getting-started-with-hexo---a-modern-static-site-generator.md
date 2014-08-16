title: Getting started with Hexo - a modern static site generator
date: 2014-04-12 15:13:19
categories: blogging
tags: 
- hexo
---

{% img img-thumbnail /images/hexo-logo.png %}

Hexo is a modern static website generator & bloging platform written in Node.js.  It is a great way to create a blog or other content driven websites as all the content is written in markdown and can therefore be versioned with Git. 

I am using Hexo for my developer blog (using blogger became very slow) and am also using Hexo for a series of online tutorials on developer tools.

Here is a quick guide to get going with Hexo.

<!-- more -->

# Install Node.js

If you havent already got node, go to [nodejs.org](http://nodejs.org/) and follow the instructions.  My own preference is to install node into a directory called **app** in the root of my home directory.

# Install Emacs (optional)

This is not a requirement for Hexo, although Emacs and Emacs Live gives a fantastic experience when writing markdown content.  Emacs is a very lightweight and full screen editor.  Emacs Live syntactically highlights your markdown content, so headings, links, bold and italic styles are shown in as you type your content.  Italic style content even displays in italic.

{% img img-code /images/emacs-live-markdown-screenshot.png %}

# Install Hexo

There is really good documentation on the [hexo.io](http://hexo.io) website, althought all you need to do to install is:

    npm install hexo -g
    
> If you install nodejs on the system path, you need to use the above command with sudo - i.e `sudo npm install hexo -g`

# Create a Hexo projects

{% img img-topic /images/hexo-workflow-commands.png %}

Create a new hexo project, I usually do this in a folder called projects in my home folder:

    hexo init my-project-name
    cd my-project-name
    npm install 

This creates a new hexo project in a folder called `my-project-name`, so use what ever name you wish here.

The `npm install` command adds tools for processing different content sources and languages used in the Hexo themes.

# Configure Hexo to your will

Your new hexo project is configured using a file called `_config.yml`.  In this configuration file you can set the basics of your website, eg title, authour, language, etc.  You can also set the public address of your website (URL).

## Blog specific configuration

If you are creating a blog website, then you can define the structure used for your blog posts.  Your posts can use any combination of year, month, day and title.  By default the posts will use all 4 combined.  I prefer to just use the year, month and title.

``` _config.yml
permalink: :year/:month/:day/:title/
permalink: :year/:month/:title/
```

You can also set the default filename, layout template (scafold) for new blog posts, when created with the command `hexo new`.

``` _config.yml 
new_post_name: :title.md # File name of new posts
default_layout: post
```

## Version your Hexo project 

If you are deploying your website to Github pages then the generated content is versioned by Github.  However, the markdown content for your websites and any configuration changes you make will not be versioned.

If you are going to use this site for any important content, I'd recommend putting the Hexo project into a github repository (or similar service).  Using version control for your content helps you track changes effectively and gives an easy way for people to correct your content using Github pull reuests.

The directories and files to add to the version control system include:

* `_config.yml` for your project configuration
* `source` directory for all the content in markdown 
* packages.json so the tools you use to generate the Hexo website will be installed when you run `npm install`

## Versioning the Hexo theme 

You could also version the `theme` folder assuming you were going to make changes to the default hexo them.  However, it is better to create a new theme which is a copy of the Hexo default change with your changes added.  Then you can update the hexo project `_config.yml` to use this new theme.

If you decide to make a lot of theme changes then it may be better to version the theme as a seperate project.  This new theme can then be copied (cloned) in from the repository you are managing the theme with, or even set up the theme repository as a git submodule.

# Running a local Hexo server

Although you wont have much content at this stage, you can still see what the website looks like by running Hexo server locally:

    hexo server 

By default this runs a node application on port 4000, so open your browser at: http://localhost:4000/

# Adding blog posts to your Hexo projects

The easiest way to add a new blog post is to let Hexo generate it for you from its template, this will ensure your post picks up the current them and any blog specific styling:

    hexo new "name of my blog post with full on SEO"

Hexo will return with the full path to the file it has created for you.  Edit this file in your favourite editor (surely this is Emacs).  Becareful to add your content after the **frontmatter**, this is the first few lines that define the title, date, style and tags used for the post.  Add your markdown 


# Adding images to your posts

If you are only going to have a few images in the Hexo project (a few hundred or so), then the easiest way is to keep them in a `source/images` directory.  Github pages has a content delivery network (CDN) that will help deliver you images quickly around the world.  You can include these image files as you version the rest of your content for the project.

If you are going to use a great many images on your website (1,000's), you may be better off keeping those images in some kind of image service (Google+ photos) or content delivery network(CDN).

Using a CDN will incure a small cost, but unless are using terrabytes of bandwidth to serve up your images this will only a few dollars a year.  Examples of CDNs [Amazon CloudFront](http://aws.amazon.com/cloudfront/), [EdgeCast](http://www.edgecast.com/), or [level3](http://www.level3.com/).  Alternatively you could use an [Amazon S3 bucket](http://aws.amazon.com/s3/), but I suggest you find a good client for that service.

# Adding pages to your Hexo website

Just like with blog posts, you can create pages using the `hexo new` command, simply by specifying the page template (scaffold).

    hexo new page "page-name"

If you want a hierachy of pages then you would have to create them manually.  It seems `hexo new` does not know how to create pages underneath other pages.  However, as its only simple markup it is generating then it is easy to copy out your own page structure using the command line or a graphical file manager.

# In Summary 

Hexo is a lightweight and fun to use platform for bloggind and similar kinds of content driven sites.  I am currently also building out developer workshop materials using Hexo.

To discover more about Hexo, visit the [Hexo area of this site](/hexo/) and the [Hexo.io](http://hexo.io) website.

Thank you.
[@jr0cket](https://twitter.com/jr0cket)

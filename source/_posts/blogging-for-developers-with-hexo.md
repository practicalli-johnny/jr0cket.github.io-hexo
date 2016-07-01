title: blogging for developers with hexo
date: 2016-06-04 13:23:08
categories: blogging
tags:
- hexo
---

{% img img-thumbnail /images/hexo-logo.png %}

Using a **Static Site Generators** like [Hexo](http://hexo.io) gives a developer a very fast blogging workflow, using familiar tools and giving the ability to write offline.  Content is written in markdown, keeping it portable between any blog generators and making it easy to version in Git. You can also use Git to deploy your site quickly, even over slow networks.
  
Static sites can be hosted anywhere and are fast to serve and easy to cache.  For example, [Github Pages](https://pages.github.com/) offers a very fast way to host your site.

Lets take a look at Hexo, my favourite static site generator.

<!-- more -->

# Blogging with Hexo 

{% img img-topic /images/hexo-workflow-commands.png %}

Hexo has a very simple workflow.  First you create a blog website: 

```
hexo init
```
This gives you a new Hexo website with a responsive design theme, a working blog and a sample article.

Then simply create new posts with the command

```
hexo new "blog post title"
```

This creates a new file under `sources/_posts/blog-post-title.md`.  Edit this file and write your blog in markdown.

You can view your blog at any time via a local hexo server.

```
hexo serve
```

As you save the blog posts you are writing you can see the changes via this local server, so you know what the site looks like before you deploy your posts.

# Deploying your blog & posts

As Hexo creates a set of HTML, JavaScript & CSS files for your blog can deploy it on any web server.

I use [Github Pages](https://pages.github.com/) to host my blog as its incredibly fast and easy to use.  Using a repository called `jr0cket.github.io` on my jr0cket account, Github Pages serves up the content at [http://jr0cket.github.io] from the `master` branch.  Hexo is configured to deploy to this repository.

Read my [getting started with Hexo](http://jr0cket.co.uk/2014/04/getting-started-with-hexo---a-modern-static-site-generator.html) article to create your first Hexo website and start writing blogs


# Customising your posts

Each post is created from a template, which you can also customise in `scaffolds/post.md` or create new templates in `scafolds`.

Here is an example template I created when writing blog posts about hexo.  It sets the category and tags as well as the topic image.  I create a new blog post with `hexo new hexo "blog post title"`:

```
title: {{ title }}
date: {{ date }}
categories: blogging
tags: 
- hexo
---
{ img img-thumbnail /images/hexo-logo.png }

Thank you.
[@jr0cket](https://twitter.com/jr0cket)
```

# Customising themes 

Landscape is the default Hexo theme and was created with responsive design principles, so it works well on all devices.  You can also use one of the many [Hexo themes](https://hexo.io/themes/) or create your own theme.

See [how I created my own version of the Hexo Landscape theme](http://jr0cket.co.uk/hexo/).

# Using Git for content & git submodules for themes

{% img img-topic /images/hexo-logo.png %}

As the markdown you write is text-based then its easy to use Git to manage versions of your content effectively.  Git can also be used to manage any theme you create. 

I created my own theme and rather than keep it in the same repository, I used Git submodules to manage theme and content changes seperately.

{% img img-code https://lh3.googleusercontent.com/-VuoPUgPuNV8/U4uIHw5YjoI/AAAAAAAAOTs/7PF8HvWrwIQ/w320-h240-no/git-submodules-concept.png %}

Read in more detail how I used [Git Submodules for managing content seperately from a custom theme](/hexo/using-git-submodules-for-custom-hexo-theme.html).

# Why not just use blogging platforms

There are a large number of blogging platforms (wordpress, blogger, etc) that initially seem quick and simple to use.  However, you soon discover their limitations and how slow they can be.  If you want to customise themes then it becomes challenging or event impossible due to restrictions.

These services require you to create your content online which depends on you having a fast internet connection as you write.  Most platforms were built several years ago, so are not always the most efficient and as they are typically database driven you end up with lots of round trip requests.  So these platforms are not great if you are traveling into work, on your way to an event or at a conference where the WiFi is not great.

There are also proprietary plugins with some of these services that tie you into them and it is not always easy to migrate to another service.

Thank you.
[@jr0cket](https://twitter.com/jr0cket)

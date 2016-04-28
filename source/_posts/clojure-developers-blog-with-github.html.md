title: Clojure developers blog with Github Gists
date: 2012-04-12 11:25:00
categories: github
tags: 
- clojure
- github
- github-gists
- coding
---

{% img img-thumbnail http://3.bp.blogspot.com/-te_MuKdFBTQ/TzFLahe2BxI/AAAAAAAAEbY/Bn_JPN_s3qU/s1600/clojure-logo-500x.png %}

Whilst [Github](https://github.com/) is a great way to share a whole repository of code, sometimes you want to talk about the design and challenges of developing your code, that discussion is often best done in a blog post.

So how do you put your lovingly crafted [Clojure](http://clojure.org/) code (or anything else) into a blog so that it looks as beautiful as it does in Emacs?  Lets take a look at Github Gists.

<!-- more -->

# Enter the [Github Gist](https://gist.github.com/)
A gist is a simple way to share code snippets with others, although unlike services like [PasteBucket](http://www.pastebucket.com/) the gists are automatically versioned, forkable and usable as a git repository.

# Adding Gists to Hexo 

Including a Gist inside a blog post is very easy when using Hexo, as it provides a special tag.  Simply get the number of your Github Gist and include it in the gist tag as follows

{% codeblock %}
    { % gist gist-id filename % }
    { % gist 37766464 project.clj % }
{% endcodeblock %}

> There should be no space between { and % or % and }

# Adding Gists to Blogger 

To add these gists to Blogger requires a bit of JavaScript and is a real pain because of how constrained Blogger is.  Luckily [Moski Doski has done the hard work](http://blog.moski.me/2012/01/gist-with-bloggers-dynamic-views.html) for us and put it on [a Github repository](https://github.com/moski/gist-Blogger) to share.

At the end of each of your blog posts, include the following code using the HTML editor:

{% codeblock lang:js %}
<script src="https://raw.github.com/moski/gist-Blogger/master/public/gistLoader.js" type="text/javascript"></script>
{% endcodeblock %}

Here is the same code as a gist:

{% gist 1649299 %}

Now to include any gist template just add the following anywhere in your blog post.

{% codeblock lang:html %}
<div class="gistLoad" data-id="GistID" id="gist-GistID">Loading ....</div>
{% endcodeblock %}

Again, the same code is available as a gist:

{% gist 1649333 %}

Replace the `GistID` with your gist id number, shown at the top of the gist you created (or gist you found and want to share with the world). 

# My own example

When I first started using Emacs I created a basic `init.el` configuration for Clojure.  This loads all the base packages you need for making Emacs 24 Clojure aware in one `init.el` file.  If you drop this `init.el` file into your `~/.emacs.d/` folder and run Emacs 24 for the first time then all the necessary packages will be automatically downloaded and added Emacs.

{% gist 2366262 clojure-init.el %}

# In Summary

Using [Github Gists](https://gist.github.com/) in your blog post is a simple way to view code in a consistent way, at the same time providing a simple way to share code and configuration with others.  

Some blogging platforms like [Hexo](http://hexo.io) make it easy to add Gists, some like [Blogger](http://www.blogger.com/) require way too much encouragement.

Thank you.
[@jr0cket](https://twitter.com/jr0cket)


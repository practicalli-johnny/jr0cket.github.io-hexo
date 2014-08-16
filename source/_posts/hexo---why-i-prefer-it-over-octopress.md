title: Hexo - why I prefer it over Octopress
date: 2014-04-02 13:55:29
categories: blogging 
tags: 
- hexo
---

{% img img-thumbnail /images/hexo-logo.png %}

There are several [static website & blogging platforms available](http://www.staticgen.com/), so why did I choose [Hexo](http://hexo.io) over things like Jekyll, Octopress, DocPad or writing my own?  Let me elaborate.

<!-- more -->

# I write more JavaScript than Ruby

Ruby is a great language but one I rarely use it for development anymore.  

The languages I use the most are Clojure and JavaScript, so ideally the tools I use should be written in one of those languages.  Why, well I already have the environment set up to support tools in those languages and if I need to extend the tool then I have the skills to do so relatively quickly.

# Ruby is a pain to install 
I have had a lot of problems with Ruby on MacOSX and Ubuntu, with only compilation from source code being successful.  This takes a bit of time and requires extra packages to be installed I otherwise wouldnt need.  RVM did strange things to my bash resource files last time I tried it out and the install failed on both MacOSX and Ubuntu.

# New is often Better

Hexo is relatively new and yet has learnt a lot from Octopres.  So has the advantage of not baking in any technical debt or having language specific quirks.  One example of why I like Hexo better is its simplicity.  To create a new file for a blog post in Hexo you use the command:

    hexo new "title of blog post"

With Octopress the command is similar but not as easy to remember and trickier to type:

    rake new_post["Title of blog post"]

The differeces are relatively small, but in terms of usabiltity I feel a big difference especially as I write several blog posts a week. 

Rather than using the command `octopress` you have to remember that you are using the command `rake`.  This is fine if you are used to Ruby every day, but I am not.  The form of the command also makes it difficult to rember (eg, that you have to use brackets and which ones were they again) and its actually harder to type, especially for a touch typist.

# Great feedback process

If you run the Hexo server then any changes you make, either to the content of your site or the design (CSS, theme, etc) is automatically picked up and rendered.  So if you are curious about how your changes look, then you just need to point your browser to the hexo server, usually running on port 4000.

So to run the hexo server you use the command:

    hexo server
    
Then to see the results you open the link http://localhost:4000/

When you make a change you get output in the console that is currently running the Hexo server, for example

{% img /images/hexo-server-example-output-on-changes.png %}

This allows me to work locally on my laptop and see the results instantaineously.  Only when I am ready to share my changes with the world do I need to generate the static content and push it to Github pages.

This simple process should support me event when I have hundereds of blog posts and pages of content.  I wont have to wait for the generation of the site (although Hexo is pretty quick anyway, generating the site as it is in about 5 seconds).

# Responsive community 

There is a healthy community around Hexo.  There are already lots of articles about configuring Hexo and creating your own themes.  I have found the project itself very responsive to issues and I even had several pull requests accepted.

# Multi-threaded processing 

As I plan to use one platform for all my static web content, blogging, tutorials, slides and technology micro-sites, then I need something that works pretty quick.

Hexo has also added a cache system to speed up the generation time even further.  The cache can be used with headers, footers or anywhere where the same content is generated repeatedly.

# Customisation 

I also want to be able to put my own look onto my websites.  Most tools of this kind provide some nice sites, but I dont want something that just looks exactly like every other site out there.

However, I dont want to spend a long time configuring themes, so it should be really easy to tweak exiting themes.  

So far I have found Hexo easier to understand the theme structure from reading the default landscape theme.  Although I dont believe there is a vast difference between Hexo and Octopress themes.  It just seems a little easier to work with than the Octopress themes, but I guess it depends which themes you work with in the end.

# In Summary

Hexo is a great choice for any blog or static website you want to create, I highly recommend switching to it and deploying your websites on Github pages.

Thank you.
[@jr0cket](https://twitter.com/jr0cket)

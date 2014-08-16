title: Hexo theme - creating image styles
date: 2014-06-20 18:38:18
categories: blogging
tags:
- hexo 
---
{% img img-thumbnail /images/hexo-logo.png %}

Adding images to a blog post helps the audience undersand what the will get from reading the article and if it will be relevant for the.  Images also aid the understanding of the topic you are covering, especially if you are explaining something technical or more complicated.

The default theme for hexo only provides a single image style, so here I will create several styles of image to help convey the topic and details of every post.

<!-- more -->

# Adding image logos to posts

I like to have logos on images to provide a quick visual way to identify the topic of an article.  This is similar to other sites such as [Slashdot](http://slashdot.org).  

If I simply add an image then it will be placed in the middle of the article area, this does not look that great and takes up a lot of space.

{% img img-code /images/hexo-theme-image-default-style.png %}

To make better use of space and improve the design, I created a style called `img-thumbnail`.  The style ensures that each image displays on the left and be no bigger than 240 pixels wide and 96 pixels high.
 
{% codeblock lang:css /themes/landscape/source/css/_partial/article.styl %}
  .img-thumbnail
    max-width: 240px
    max-height: 96px
    display: block
    margin-right: 12px
    margin-top: 12px
    float: left
    clear: left
{% endcodeblock %}

Here is an example of what the `img-thumbnail` style looks like in the websites

{% img img-code /images/hexo-theme-images-style-thumbnail.png %}

# Adding image style for screenshots 

Some images will be screenshots of the command line, code and developer tools in actoin.  These images will be centrally placed as normal, but will have specific height and with contraints to make sure all the images are big enough to view yet stil fit on the page.

{% codeblock lang:css /themes/landscape/source/css/_partial/article.styl %}
  .img-screenshot
    max-width: 640px
    max-height: 320px
    display: block 
    margin-left: auto
    margin-right: auto  
{% endcodeblock %}

Here is an example of what the `img-screenshot` style looks like in the websites

{% img img-code /images/hexo-theme-image-code.png %}

# Adding images for topics discussed

During an article I may talk about several different topics and what to visually highlight what topic is being disscussed.  So again I created another image style, this time placing the image on the right hand side of the content and allowing a bigger size.

{% codeblock lang:css /themes/landscape/source/css/_partial/article.styl %}
  .img-topic
    max-width: 360px
    max-height: 1800px
    display: block 
    margin-left 12px
    margin-right: 12px
    float: right
    clear: right
{% endcodeblock %}

Here is an example of what the `img-topic` style looks like in the websites

{% img img-code /images/hexo-theme-images-style-topic.png %}

# In Summary

By setting up different styles it makes it very easy to layout images in an article, using just one style name.  This helps me make each blog post more visually appealing to look at and therefore a better experience for the reader (and myself).

Thank you.
[@jr0cket](https://twitter.com/jr0cket)

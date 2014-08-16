---
layout: post
title: "Creating content in markdown for your Octopress blog"
date: 2014-03-13 19:32:20 +0000
comments: true
categories: blogging 
tags: octopress
---

Octopress enables the creation of great looking blog post using simple markdown text.  This gives you a no-fuss way of writing your blogs without getting distracted.  Here I will cover how to add formatting to you text and embedding code and other useful media into your blog posts.

{% blockquote %}
In my previous blog on Octopress I covered the blogging workflow and the handful of rake commands that help you create and deploy your blog posts consistently. 
{% endblockquote %}

<!-- more -->

## Adding styles to text

Headings
Bold, italic 


## Adding images 

Images are always a good way to explain concepts or to just get attendtion for your writing.

To add an image to your post, you add the following code 

{% codeblock [Insert an image in your post] http://octopress.org/docs/plugins/image-tag/ %}
  {% img [class names] /path/to/image [width] [height] [title text [alt text]] %}
{% endcodeblock %}

Here is an example with my two cute cats:

{% img /images/kittens-snuggled.png %}

### More examples 
{% codeblock %}
  {% img http://placekitten.com/890/280 %}
  {% img left http://placekitten.com/320/250 Place Kitten #2 %}
  {% img right http://placekitten.com/300/500 150 250 Place Kitten #3 %}
  {% img right http://placekitten.com/300/500 150 250 'Place Kitten #4' 'An image of a very cute kitten' %}
{% endcodeblock %}


## Showing code 

### Code blocks 

You can embed code snippets directly in the markup of the blog posts you write using the codeblock directive.
http://octopress.org/docs/plugins/codeblock/

These are okay but I have not figured out a way to stop Octopress examples from rendering incorrectly (unless there is an Octopress update that fixes this)

[TODO - figure out how to show code snippets that are also liquid calls]

### Github Gists

I am used to using Github and Gists for sharing and collaborating around code, so as Octopress can use Gits then I have started using the gist directive.
 
{% gist 9532424 %}

See the [http://octopress.org/docs/plugins/gist-tag/](Octopress article on Github gists) for a few more examples.


## Adding Video

You can add embedded videos from YouTube and Vimeo very easily, you just need to know the id of the video which is the last characters of the 

For example, there is a great video by Lindsey Stirling at https://www.youtube.com/watch?v=DHdkRvEzW84, so to include this video in a post I would use the video id at the end of that web address (after the watch?v=).  So I would add the following code to my code

{% raw %}
  youtub DHdkRvEzW84
{% endraw %}
  
You can use either YouTube or Vimeo for your video souce using the following syntax:
 
{% raw %}
   youtube video-id
   vimeo video-id
{% endraw %}


### Example

A beautiful video with amazing music from Lindsey Stirling:

 {% youtube DHdkRvEzW84 %}


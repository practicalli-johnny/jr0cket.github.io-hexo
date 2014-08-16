title: Hexo custom theme - styling code snippets
date: 2014-06-04 06:34:28
categories: blogging
tags: 
- hexo
---

{% img img-thumbnail /images/hexo-logo.png %}

The hexo theme shows code in a solid black box with syntax hightlghting to match.  It gives a nice contrast to the rest of the content, however I wanted to add curves to the corner of the code boxes.  I also wanted to  add a margin / padding around the code box so it did not touch the edges of the post.

<!-- more -->

# Add corners to the code box 

Values for commonly used styles are defined as variables in the file `source/css/_variables.styl`.  This makes it easy to redefine a style across the whole theme with a single change.

In this case, I defined a `code-border-radius` variable and gave it a value of 10px.

{% codeblock source/css/_partial/header.styl lang:css %}
 code-border-radius = 10px 
{% endcodeblock %}

I edited the `source/css/_partial/highlight.styl` file and added definitions to the `$code-block` style: 

* `boarder-radius` adds a cure to the corner using size defined in the variable `code-border-radius`
* `background: #333` - why did I add this ?
* `margin: 1px 10px 1px 10px` puts a space of 10 pixels at the left and right of the code block, as well as a 1 pixel space above and below
* `border: 3px solid #EEEEEE;` adds a discrete white boarder around the codeblock to make it blend into the page gracefully.

The updated `$code-block` style now looks like (added lines 11-14):

{% codeblock source/css/_partial/highlight.styl lang:css %}
 $code-block
   background: highlight-background
   margin: 0 article-padding * -1
   padding: 15px article-padding
   border-style: solid
   border-color: color-border
   border-width: 1px 0
   overflow: auto
   color: highlight-foreground
   line-height: font-size * line-height
   border-radius: code-border-radius
   background: #333;
   margin: 1px 10px 1px 10px
   border: 3px solid #EEEEEE;
 {% endcodeblock %}
 
 
 I didnt make any further changes in to the theme in the `highlight.styl` file.  However, there are other things in this file you may want to modify.
 
 ## Line numbers 
 
 The hexo theme makes the line numbers smaller in font size and makes the numbers look faded by using colour number 666.  This looked good to me, so I didnt change these styles.
 
 {% codeblock source/css/_partial/highlight.styl lang:css %}
 $line-numbers
  color: #666
  font-size: 0.85em
 {% endcodeblock %}


## More customisation possible

There is a whole range of settings that affect the code-block and other highlighted areas of articles in the `highlight.styl` file, however I did feel the need to make any changes here.  

If I get tired of the black background for code I could change it here, although I'd need to check the colours used for syntax highlighting still worked with the new code background.
  
 {% codeblock source/css/_partial/highlight.styl lang:css %}
 .article-entry
  pre, code
    font-family: font-mono
  code
    background: color-background
    text-shadow: 0 1px #fff
    padding: 0 0.3em
  pre
    @extend $code-block
    code
      background: none
      text-shadow: none
      padding: 0
  .highlight
    @extend $code-block
    pre
      border: none
      margin: 0
      padding: 0
    table
      margin: 0
      width: auto
    td
      border: none
      padding: 0
    figcaption
      clearfix()
      font-size: 0.85em
      color: highlight-comment
      line-height: 1em
      margin-bottom: 1em
      a
        float: right
    .gutter pre
      @extend $line-numbers
      text-align: right
      padding-right: 20px

 {% endcodeblock %}
 
 

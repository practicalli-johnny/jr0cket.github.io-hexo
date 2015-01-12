title: Hexo codeblock highlighting verses markdown
date: 2014-03-29 01:02:50
categories: blogging
tags: 
- hexo
---

{% img img-thumbnail /images/hexo-logo.png %}

This is a simple post to see if there are any differences in the style of code when defined in a `{ % codeblock % }` or using markdown notation (tripple backticks / indentation).  In this case I am just using some simple Clojure code.

<!-- more -->

## Showing code by indentation

I have wrapped the following lines by three backtick characters on the line before and line after the code.  These tripple backtick characters to instruct the Hexo markdown processor that the containing lines should be rendered as a code block.

``` clojure really-simple-example.clj
(defn clojure-function [paramter]
  (str "Lets do something simple using Clojure and " parameter))
```

That should be a simple Clojure example using markdown indentation.  

## Using Hexo Codeblock 
Hexo has several plugin types from Swig that you can use in your post.  Lets try out `codeblock` to see if there is any difference in how it renders compared to the above markdown.

{% codeblock basic-clojure-example.clj lang:clojure %}
(def authors [:name "John Stevenson"])

(defn show-author [authors]
  (str authors))
  
(show-author authors)
{% endcodeblock %}

The rendering of both pieces of code is pretty much the same, except with the code block I added language and a title.  If I use three backticks then I can specify the language and a filename that contains the code.  If I just use indentation, specifying a language and filename is not possible (as far as I know).

Thank you.
[@jr0cket](https://twitter.com/jr0cket)


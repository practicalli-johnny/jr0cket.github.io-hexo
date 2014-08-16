title: Testing Hexo themes
date: 2014-03-29 01:02:50
categories: blogging
tags: 
- hexo
---

{% img img-thumbnail /images/hexo-logo.png %}

Lets see how different themes look like when in Hexo.  This is just some basic content to help me see what they look like with content.

## Trying out code

I wonder what code looks like when you look at it in this theme:

    (defn clojure-function [paramter]
      (str "Lets do" " " "something simple" ", " "using Clojure"))


That should be a simple Clojure example using markdown indentation.  Lets try using a codeblock to see if there is any difference.

{% codeblock %}
(def authors [:name "John Stevenson"])

(defn show-author [authors]
  (str authors))
  
(show-author authors)
{% codeblock %}

## More content 

I should add some images of the themes:

### Winterland

To install the theme

    git clone git://github.com/winterland1989/hexo-theme-winterland.git themes/winterland

The theme looks like:

{% img hexo-theme-winterland.png %}

This could be an interesting theme to tweak for my own xmas theme to use during december each year.

Thank you.
[@jr0cket](https://twitter.com/jr0cket)


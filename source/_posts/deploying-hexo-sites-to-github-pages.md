title: Deploying hexo sites to Github pages
date: 2014-03-27 09:32:32
tags:
---
{% img img-thumbnail /images/hexo-logo.png %}

Hexo is a great way to easily generate content and publish it use Github pages. 

{% blockquote %}
See my previous articles on setting up [Hexo](/tags/hexo) and creating content
{% endblockquote %}

<!-- more -->

## Configuring your site name

Its important to add the URL of your github pages site to the Hexo configuraiton 

{% codeblock _config.yml %}
# URL
## If your site is put in a subdirectory, set url as 'http://yoursite.com/child' and root as '/child/'
url: http://jr0cket.github.io/hexo-blog-test
root: /hexo-blog-test/
{% endcodeblock %}

If your project uses a sub-folder, Make sure that the root line has a trailing forward slash, otherwise your URL paths will not be correct.

Projects use a sub-folder if they are deployed to the gh-pages branch of a repo.  When you are using the main repo for a user or org (username.github.io or org-name.github.io) then these repos run the Github pages from the master branch, so no root should be required (except for a single forward slash which is set by default in hexo)

### Example

```
root: /hexo-blog-test  
```

This will give /hexo-blog-test2014-name-of-blog-post and wont show the page up or if it does then probably wont include the CSS styles


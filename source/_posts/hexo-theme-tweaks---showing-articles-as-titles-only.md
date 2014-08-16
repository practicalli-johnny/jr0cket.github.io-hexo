title: Hexo theme tweaks - showing articles as titles only
date: 2014-04-16 09:59:33
categories: blogging
tags: 
- hexo
---
{% img img-thumbnail /images/hexo-logo.png %}

Hexo displays posts in a summary format by default, showing the title and content of the article up to the point where the `more` marker is used:

<!-- more -->

I like this summary format for the main page as its where people tend to browse a little more and usually want a little more information to help them decide if they want to read the whole article.  

[TODO: Insert picture of summary layout]

However when someone selects the archive, category or tags section, they are most likely looking for something specific and so just showing the titles of the posts helps them scan the articles quickly.

So this article we will cover how to modify the default Hexo theme, landscape, to show summar and title only views.

<!-- more -->

## Understanding the layout 

Layout of the page is defined mainly in [EJS](https://github.com/visionmedia/ejs) format and then imported via the `theme/landscape/source/css/style.styl` file that is used to pull together a single `style.css` file for the whole site (once the site is generated).

All pages use the default `index.ejs` [is it index or layout - check the hexo docs] as a base template, over-riding it where desired.  For the front page of the blog this is fine.

The archive, categories and tag pages all use the same code, however these are the files we are going to change

    theme/landscape/layouts/_partial/archive.ejs
    theme/landscape/layouts/_partial/category.ejs
    theme/landscape/layouts/_partial/tag.ejs

Lets first find out what changes need to be made and in what file.


## Using Chrome developer tools

You can use the Chrome developer tools to find out the secion of CSS that controls the displaying of the summary part of the article.


It turns out this summary part of the content is managed by a section called `article-entry`.  This is included in the file `theme/landscape/layouts/_partial/article.ejs`:

    <div class="article-entry" itemprop="articleBody">
      <% if (post.excerpt && index){ %>
        <%- post.excerpt %>
        <% if (theme.excerpt_link){ %>
          <p class="article-more-link">
            <a href="<%- config.root %><%- post.path %>#more"><%= theme.excerpt_link %></a>
          </p>
        <% } %>

I tested that this was the code rendering the article summary using the Chrome developer tools.  I right-clicked on the first line of the code, the opening **div** tag, and selected `delete node` 
{% img /hexo-themes-test/images/hexo-theme-tweak-devtools-delete-node.png %}


## Making the changes to the theme 

There may be better approaches than I have taken, however mine is fairly straight formward.  I simply take a copy of the archive.ejs file and called it archive-titles.ejs.

I then remove the above code completely from the `articles-titles.ejs` file and call that file instead from the `archive.ejs`, `category.ejs` and `tag.ejs` files.

So the archive, catagory and tag files are changed calling the archive.ejs:

    <%- partial('_partial/archive', {pagination: 2, index: true}) %>

and now call `archive-titles.ejs`:

    <%- partial('_partial/archive-titles', {pagination: config.archive, index: true}) %>

With `hexo server` running these changes are picked up straight away, so we can easily see if the changes worked as expected

[TODO: image of changed archive]

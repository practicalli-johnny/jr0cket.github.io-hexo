title: Create content for your Hexo Website  
date: 2014-07-13 16:06:00
---

{% img img-thumbnail /images/hexo-logo.png %}

Hexo can create pages and blog post files for you using the `hexo new` command, so your content is created in a consistent way.  If you want to create a new post you use the command:

    hexo new blog-post-name

If you want to create a page

    hexo new page page-name

# Customising the Hexo templates 

Hexo uses templates in the `hexo-project/scaffolds` directory.  You can edit these files and create your own templates.  If you create a template with a file name `scaffolds/hexo-post.md` then you create a new post using this template with the command `hexo new hexo-post blog-post-name`.

I want all my posts to have the same signature at the end, which includes a thank you and a link to my twitter account.  So I edited the existing Hexo template for blog posts and added a few lines.

    Thank you.
    [@jr0cket](https://twitter.com/jr0cket)

Now when I create a new blog post with `hexo new blog-post-name` it automatically has the extra content from the template.

> At the time of writing, templates do not support swig includes, so its not possible to include an image.  A work-around is to  miss the `%` characters and just use `{ img /images/logo.png }`, then add the `%` caracters back once the blog post has been created.

[Back to Hexo overview](index.html) | [Next: Run your Hexo website locally](run-your-hexo-website-locally.html)





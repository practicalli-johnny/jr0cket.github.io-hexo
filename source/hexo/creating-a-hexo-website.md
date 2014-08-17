title: Creating a Hexo website  
date: 2014-07-10 17:01:00
---

{% img img-thumbnail /images/hexo-logo.png %}

Once you have [hexo installed] it is easy to create a new project for a website.  Create a new website projct using the hexo init command, giving the name of your project:

    hexo init my-hexo-website

You will now have a new directory called `my-hexo-website`.  

> I am going to deploy my Hexo webstie as the main website on github pages, so I called my project `jr0cket.github.io-hexo`.  Therefore I used the command `hexo init jr0cket.github.io-hexo`.  The generated content for my hexo project will be pushed to a Github repository called `jr0cket.github.io` and viewed at [jr0cket.github.io](http://jr0cket.github.io).

Now you need to add the node modules to help you generate your website from the content you write.  When you create the Hexo project, a file called `package.json` is also created that lists all the packages required for Hexo.  So change into the new directory you created and use the node package manager to install the packages

    cd my-hexo-website
    npm install

This completes the creation of your hexo project and you can use the command `hexo server` to immediately see your new website.

# Deconstructing a Hexo project 

The important files and directories to know abou tin a hexo project are as follows:

* `_config.yml` - the main configuration file for Hexo 

* `package.json` - lists the required packages to make Hexo generate content for your project.  Running the command `npm install` within your hexo project downloads these node modules and puts them into folder called `node_modules`

* `.gitignore` - lists files and directories that should not be included if you put your project under version control.  Without using the force flag `-f` you wont be able to add any of the files listed in `.gitignore` when using `git add` or `git -am commit`.

* `scaffolds` - layout templates used when you create content with the `hexo new` command.  You can define your own templates by creating additional markdown files with _frontmatter_ definitions and any common markdown you wish to include.  For example, I add a signature to the bottom of my posts that links to my twitter account.  See the other files in the scafold directory for examples.

* `source` - this directory contains all the content you write as markdown.  You can ask Hexo to create files for you using the templates in scaffolds, for example `hexo new blog-article` to create a new blog post or `hexo new page clojure` to create a new page on Clojure.  Blog posts are placed under the sub-directory called `_posts` and pages create a sub-directory with the name of a page and a file in that sub-directory called `index.md` 

* `themes` - this directory contains the default Hexo theme called Landscape.  You can try other themes for Heox by cloning them into the themes directory inside a sub-directory called by the theme name.  If you wish to add or change the top level navigation on you Hexo site, you will need to edit the configuration file of the theme you are using, eg `my-hexo-website/themes/landscape/_config.yml`.

[Back to Hexo overview](index.html) | [Next: Managing your Hexo website with Git and Github](managing-hexo-website-content-with-git-and-github.html)


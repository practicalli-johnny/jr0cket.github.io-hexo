title: Customising the Hexo theme
date: 2014-07-02 21:37:14
---

Whilst I lke the [Hexo theme landscape](https://github.com/hexojs/hexo-theme-landscape.git), the default theme for hexo, I plan to make a lot of changes to it in order to maximise the space and add my own design touches.

> If you only want to create a few additional entries in the top navigation bar, you can simply add them to the configuration file for the theme `hexo-project/theme/landscape/_config.yml`.  No need for your own theme if this is all you want to do.

# Guides to Create a custom theme

Here are a series of guides showing how I changed diffent aspects of the Heroku default them, landscape.

* Create a new theme bye Forking the Hexo landscape theme
* Updating the hexo project configuration to use the new theme.
* Strealining the title & changing the graphic
* Defining additional items on the top navbar - links inside your hexo website and external websites
* Changing to the Ubuntu font
* Adding Font Awesome Icon graphics for social media links
* Creating different image styles - for topic, thumbnails, code, etc...
* [Using Git submodules for the customised theme](using-git-submodules-for-custom-hexo-theme.html) - why use a submodule over just cloning the repository


# Creating your own theme

  Rather than build a new theme from scratch, I am going to base my new theme on the default Hexo theme called Landscape.  The Landscape theme has a responsive design and provides much of the design & layout I want from my theme.  Using Landscape as a starting point will also give quicker visual feedback for my changes.

## Forking the Hexo theme
To create my theme based on Hexo Landscape theme, I first fork the [hexo-theme-landscape repository](https://github.com/hexojs/hexo-theme-landscape.git) on Github by pressing the fork button on its repository page.

As this is a seperate project I am renaming my fork.  In the settings for my fokrked repostior, I change the name of the repostory to **hexo-theme-landscape-jr0cket**

Then to work on the theme I clone my forked repository into the hexo project for my main website

    git clone https://github.com/jr0cket/hexo-theme-landscape-jr0cket.git hexo-project/theme/landscape-jr0cket

Now I can edit the theme as I am building my new website and put all my theme changes into version control as I go.  This helps me track what changes I made from the original theme and easily roll back any changes should I need to.

## Hexo theme updates

There maybe updates from the original theme I want to incorporate with my new theme, so I also add the repository from the original hexo-theme-landscape to my local clone

    git remote add original-theme https://github.com/hexojs/hexo-theme-landscape.git

Then if there are updates to the original theme, I can create a new branch in my local repository and pull the changes to the original landscape theme in using Git:

    git checkout -b original-theme-updates
    git pull original-theme master

As I am on a new branch, `original-theme-updates` I can see the affects of these updates on my website straight away - as I always have `hexo server` running on my site.  The `hexo server` process picks up any changes immediately and so if I change between the two branches, all I need to do is refresh the browser pointing to my local site and I can see what has changed.

To see the specific code changes I can do a diff between my `master` branch and the `original-theme-branch`.  If there are any changes I want to keep then I can merge them into master.

> Merging specific commits from one branch to another is a Git technique called cherry picking.



[Back to Hexo overview](index.html) | [Using Git Submodule to manage your custom Hexo theme](using-git-submodules-for-custom-hexo-theme.html)

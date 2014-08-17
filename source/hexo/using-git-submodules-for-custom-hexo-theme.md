title: Using Git Submodules to manage your custom Hexo theme
date: 2014-07-02 21:37:14
---

{% img img-thumbnail /images/git-logo.png %}

I [use Github to manage the content for my Hexo website](managing-hexo-website-content-with-git-and-github.html). I also use Github to develop my own custom theme by forking the Hexo Landscape theme repository.  This gives me two distinct repositories to work with:

1. **hexo repository** - my content
2. **theme repostitory** - my custom theme

By making the theme repository a Submodule of the hexo repository I can work with all the files in one place, stil maintaining two seperate Git change histories.  The `git submodule` command adds all the files from the theme repository into a directory in the hexo module, as if they were all part of the same project.

This guide will show you how to set up a custom theme as a Submodule of the Hexo Git repository. 

# Configuring the Theme repository as a Submodule

Inside the hexo project repository, add the theme repository as a Submodule using the command

    git submodule add git@github.com:jr0cket/hexo-theme-landscape-jr0cket.git themes/landscape-jr0cket

The submodule command clones the theme repostiory from the given URL, into the directory specified: `themes/landscape-jr0cket`.  All the files from the theme repository are now part of the hexo project.

{% img img-code /images/hexo-theme-git-submodule-add-status.png %}

> The git submodule command adds a new reference to the theme repository to the local hexo repository configuration file.  This points to the latest commit of the theme repository.

# Capturing changes to the Theme repository

{% img img-topic /images/hexo-submodules-theme.png %}

As I develop my custom Hexo theme, I make changes to the styles and layout of the design.  Inside the `theme/landcape-jr0cket` I can commit these changes to the theme repository (the submodule) in the usual way using `git add` & `git commit`

I can also push those commited changes to the theme repository on Github using `git push origin master`.

# Updating the Hexo repository to the latest theme version

As you add changes to the theme, they appear in the hexo project simply because they are there on the same filesystem.  Anyone who clones the hexo repository would only get the version of the theme when the submodule created.  So to update the hexo repository with the new theme version, simply add the submodule as a change to a commit in the hexo repository.

Using `git status` you will see the directory name for your submodule is marked as modified.  Add this as normal using the `git add` and `git commit` commands as normal.

    git add theme/landcape-jr0cket
    git commit -m "theme update with x, y and z"

# Cloning the project with a submodule

If I work on another laptop or someone else is going to work on the hexo project, then all that is needed is to clone the hexo repoisitory.

    git clone git@github.com:jr0cket/jr0cket.github.io.git

The cloned hexo repository has a reference to the theme submodule, although you still need to get the actual files for the theme.  This requires two git commands after the clone command

    git submodule init
    git submodule update

Now you have the theme repository as part of your project, with all the files.  

> The version of theme will be the one added to the hexo project when the submodule was first added or the last commit of the theme submodule to the hexo repository.

# Summary 

When just using one submodule, there is not much difference in the amount of work need to do compared with having two seperate modules.  However, as you add several submodules or many more people sharing the project the advantages and time saved grows.

# References

* [Git SCM Submodule tutorial](http://git-scm.com/book/en/Git-Tools-Submodules).  
* [John Cairns Git Submodules tutorial](http://joncairns.com/2011/10/how-to-use-git-submodules/)

[Back to Hexo overview](index.html) | [Deconstructing the Hexo theme](deconstructing-the-hexo-theme.html)




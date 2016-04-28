title: GitIgnore for Clojure and Emacs - ignore Emacs backup & temp files
date: 2012-12-13 08:00:00
categories: git
tags: 
- clojure
- emacs
- git
- dev-tools
---

{% img img-thumbnail http://git-scm.com/images/logo.png %}

Once little self-inflicted annoyance I found was when working with Git was committing temporary and backup files that my development tools create.  Yes, I should pay more attention and not just do a `git add .` but when you are head down coding then its easy to include a few things you dont need.

<!-- more -->

Whilst I could simple add patters to the git repository `.gitignore` file, this is not very effective for three reasons.

1.  I'm adding my own preferences to a project I'm sharing with others, who may have different toolset.

2.  I have to add this to each new project I create / clone / fork3.  Pull requests can be blocked up by changes to `.gitignore` files

After a little more discovery with Git, I found that `.gitignore_global` is a better way to exclude files that were specific to my tools and environment than individual project `.gitignore` files.

# Creating my own global ignores

Emacs is the tool I used for my Clojure development, as well as writning contnet in markdown and Org-mode.  As all these types of files are versioned in Git, then there is a lot of potential for backup files to sneak in.
 
So in the `~/.gitconfig` of my home directory I have a section called [core] where a global excludes file is defined

    [core]
        excludesfile = /Users/jstevenson/.gitignore_global
        editor = emacsclient

By adding file name patters to the `.gitignore_global` file for Emacs, I can add my own personal excludes without adding unneccessary stuff to each project I work on.  It also means its one less thing to remember when I am working with git projects.

{% img img-thumbnail http://1.bp.blogspot.com/-PLeobToC6lc/TzFJCfBSLPI/AAAAAAAAEbE/zSx1cOgHzZE/s1600/emacs128x128icon.png %} 

My `~/.gitignore_global` file now contains the following filename patterns, the last three patterns are specifically for the Emacs temporary and backup files.

    *~
    .DS_Store
    *~
    *#
    .#*

# Keeping project .gitignore files clean

Now when I work with Clojure projects using Emacs, I can commit away without having to worry about my editor add things that I carelessly add when in a hacking frenzy!

This also keeps the `.gitignore` files specific to a project much smaller and project specific.

```
pom.xml
*jar
/classes/
/.lein-deps-sum
/.lein-failures
/.lein-env
/checkouts
/.env
/target
```

Finally, by minimising the changes in the project `.gitignore` file then this limits the amount of times that file needs to be committed to the version control system.  Therefore it is less likely that a change in the `.gitignore` file end up in code change commits.

Thank you.
[@jr0cket](https://twitter.com/jr0cket)

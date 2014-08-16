title: Staging Patches for cleaner Git commits
date: 2014-07-15 22:58:36
categories: dev-tools
tags:
- git
---

{% img img-thumbnail /images/git-logo.png %}

Some times you work on your code or configuration files and realise you have made more changes than sensibly fit into one commit.  Using patches you can easily select only the changes want rather than adding all the changes in a file.  You dont even have to create a seperate patch file.

<!-- more -->

You can use the git via the interactive mode, however its just as easy to use the `git add -p` .  The `-p` option allows you to select what git calls _hunks_, lines git sees as a change within a file.  A hunk may be a change to one line or changes across several lines grouped together. 

    git add -p .

This command will prompt to you accept each _hunk_ through all the files that have modifications since the last commit.

If you just want to pick out changes from a specific file or collection of files you can narrow the scope by specifying the filename or filename pattern

    git add -p filename
    git add -p *.md 
    git add -p config.*

# An example

In this example there are several lines of changes in the `article.styl` file.  Using the `git add -p` command we are shown each _hunk_ in turn as a diff, so we can compare the current version with the changes in the _hunk_.  We then decide if we want to add the changed lines or not.  

We say yes to the first _hunk_ and no to the second.

{% img img-code /images/hexo-theme-git-staging-patches.png %}

Once we have added or ingnored all the _hunks_ in the file the interactive staging ends.  If we are ready we can then do a commit as normal.

# Splitting the hunks

Sometimes git chooses hunks that include too many changes.  If we see a hunk we want to break down during the interactive staging, we can select the `s` option.  We are then shown the same _hunk_ aft it has been split.

In the following example, our editor has added a new line to the file that we added a twitter account to.  We only want to add the twitter account, so split the hunk to get the twitter line as its own _hunk_.

Then we add the _hunk_ with the twitter change in it by selecting `y` and do not include the new line change by skipping the next _hunk_ by pressing `n`.

{% img img-code /images/git-staging-interactive-split-hunk.png %}

# More Interactive Staging options

There are many more options to help you when your are staging changes interactively.  Using the `?` key at any time during interactive staging will show you a brief description of those options.

{% img image-code /images/git-staging-interactive-options.png %}

For more detailed descriptoin of interactive staging and the options available, see the git manpages via the command `git help add` or [git add documentation online](http://git-scm.com/docs/git-add).

# In Summary

By staging patches I can very easily see the exact changes I am assembling for my next commit.  I can then include only the code & configuration changes that are ready to be part of the next commit.

Using this patch technique for staging avoids unstaging files (git reset -soft), editing them and then adding them again.  That is a real pain.

And finally, staging patches keeps my commits nice and simple and focused.  I get a detailed and accurate history of my changes and that makes its really easy for others to merge or cherry-pick my commits.

Read the [Git-scm guide on Interactive Staging](http://git-scm.com/book/en/Git-Tools-Interactive-Staging) if you want to see more tooling around this topic.

Thank you.
[@jr0cket](https://twitter.com/jr0cket)

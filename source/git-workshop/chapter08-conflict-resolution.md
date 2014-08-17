<link href="index.css" rel="stylesheet" type="text/css">

# <a id="top">Conflict resolution - managing the merge process</a>

During the development of your project you will make many changes to your files.  If you follow the "commit early, commit often" idea, then most of your commits should be straight forward.

Git is very good at merging changes together, although it has its limitations.

The longer you leave a change to be commited or the bigger the change is you are making (especially to existing files), the more likely you will have to manage the merge process yourself.  
  

## A common merge conflict with Github

When you create a new repository on Github you are given the choice of creating a Readme.md file and a .gitignore file for one of numerous languages.  These are both really useful things to have.

However, if you already have a repository locally with a number of commits, when you create a github repository with these files then you are actually making a commit on the github repository as well.

This leaves you with commits locally that you dont have on your github repository and a commit on your Github repository that you dont have locally.  As the commit is newer on the Github repository, then git will not push your local changes as it will not create a "fast-forward" commit.  A fast-forward commit is newer than any existing commits in that repository.

To resolve this conflict, you have to pull the change you made in the Github (addint a Readme.md and/or .gitignore file) to your local repository.  This is done with the ommand:

    git pull <repository> <branch>
    git pull github master

As your changes are out of sync between the local and Github repository, then you will have to manually merge those changes.

Assuming you did not create a Readme.md or .gitignore file locally, then when you pull you should be able just *git add* the additional files and commit them with *git commit*.  Then you can finally push all these changes up to the Github repository.

If you already had either the Readme.md file or .gitignore file locally, when you do a git pull the text from both versions of the file will be combined, with <<<<<<<<<<<<<< >>>>>>>>>> markers denoting which text comes from which version .

There is also a nice page on [Github help on dealing with non fast-forward errors](https://help.github.com/articles/dealing-with-non-fast-forward-errors
).  


## Working with pull requests
If you have a pull request that cant be automatically merged.  A committer on the project can offer suggestions on how the submitter can fix the pull request so it can be merged.  This typically includes:

* ensuring the submitter of the pull request has pulled all the changes down from the latest version of the original project.
* merging any changes between their code and the original project

Once any merge conflicts are resolved, the submitter of the pull request can do another commit locally and to their forked repository on github and that will update the pull request automatically.


[Back to top...](#top)

[Workshop homepage](index.html)

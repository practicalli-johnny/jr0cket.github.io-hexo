
# Working with Staging

## Removing changes from Staging
Sometimes you add things to staging that you change your minde about.  

If a file is untracked by git (its never been part of a commit) then you can remove it from staging using the command

git rm --cached filename

If the file has been tracked by git, then the above command will cause the file to be removed from the repository should a further commit take place.

Therefore, for tracked file that you want to unstage, you should use the command

git reset HEAD filename



# creating branches
## commiting
## merging
## remote branches
## deleting remote branches
## deleting local branches
## git remote purge


# Working with Tags
## creating Tags
## git push --tags 

# Commits
## discarding a local Commits
## discarding a remote commit and resetting your local working copy 
git reset --hard HEAD^
git checkout master



# Git Log - Updating details about Remotes

(see git-live script)

Use git fetch --all or git remote update to get details of all the changes from every remote repository attached to the local git repository you call the command from.




# Testing branches

Say you want to test out your branch you have been working on but your setup is only configured to work on master, then you can push a branch from one repository to the master (or any other branch) of another repository.


For example, heroku only deploys from master.  You can use git to deploy your *developing* branch to your *heroku-test* application using the following notation:

    git push repository local-branch:remote-branch

    git push heroku-test developing:master

In this example we are pushing the local *developing* branch to the master branch of the heroku-test remote repository.  This allows you to use heroku-test application to run some web application tests (eg. selinum).  

You dont need to merge your developing branch until after you are happy with oyour testing.



# Rebase or not rebase, that is the question

## what is Rebasing
Rebasing is a way to do merging without including specific commits that would otherwise appear due to a merge.

Some teams decide that having extra commits just for merges polutes the history of the project and makes it harder to understand.


## Why would you do it
If you are just starting with Git, then you probably dont want to do this yet.  Make sure you are comfortable with branching and merging before starting to rebase.

Rebasing can work well with short lived branches where merges would otherwise happen very often, leading to a high ratio of merge commits.  For these shor lived branches, using rebase helps keep a clean history.

If you want to keep a branch up to date from master and dont want to include lots of commits only there because of a merge, then rebase will tidily keep your branch up to date.  This makes sence if the branch is going to be around for a little while or there is active development on the master that you need to keep up with.

For branches that have been around for days or weeks, its more likey that you will benefit from a merge.  With a merge you get the full history detail, so its easier to see where things come from if there is a problem merging.

Use rebase with care as you are re-writing history and loosing some information about where changes have come from.  Make sure you dont need to know the information you are ommitting with rebase.  


# Interactive Rebasing


## merging two commits together

If you have done two commits that should really be one, then you can use rebase interactive to join those commits (squash them in git terms).

''''''
# intractively rebase the last three commits  
git rebase -i HEAD~2
''''

# an editor opens up and lets you edit the commits, in this case, the last commit will be merged into the one before it.
pick 4b65a5a Add tests
pick f239187 Implement poodles
squash c3f863f Add title to poodle page



# Git attributes file
Tell git how to manage particular file types

For example:

* text=auto 
*.rb text
*.js text 
*.bat text eol=crlf 
*.sh text eol=lf

*.png binary
        



# Submodules


## Avoid double pushing
As we have seen, when you make changes to a submodule, as well as pushing the changes in that submodule you also need to push the parent repository.  The parent has a reference to a SHA of what it knows as the latest commit for the submodule.  If the parent is pushed without the submodule, then the new commit refered to by the parent is not present in everyone elses repository.

Manage this automatically using the --recurse-submodules option on-demand
 
    git push --recurse-submodules=on-demand



Create an alias for this option so that you dont have to type it all (or remember it all if you pick a meaningful alias)

    git config alias.pushall 'push --recurse-submodules=on-demand'    





additional topics

    Repositories
    Commits
    Viewing changes
    Alias
    Going forward to fix mistakes
    Tags
    Remotes
    Github
    Branching & merging - when to do it
    Stashing
    Rebasing is evil !!!
    Cherry picking
    Patches
    Bisect
    Rerere
    Blame
    Common workflows
    Continuous Integration with Travis

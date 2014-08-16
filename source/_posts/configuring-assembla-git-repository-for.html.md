title: Configuring Assembla git repository for LSUG Scala dojo
date: 2010-06-01 17:28:00
categories: dev-tools
tags: 
- git
- scala
---

{% img img-topic http://upload.wikimedia.org/wikipedia/en/8/85/Scala_logo.png %}

This is an outline of how I have set up the git repository on the London Scala user group dojo workspace, hosted on assembla.com.

> See the[ lsug-dojo workspace for details of checking out dojo code](http://www.assembla.com/code/lsug-dojo/git/repo/instructions).
 
<!-- more -->

# Configuring access to the code repository

You need to add a public key to your assembla account in order to committing source code.&nbsp; This key is specific to the machine you created it on.

To create the key on Ubuntu you use the the `ssh-keygen` command which is installed by default in Ubuntu.&nbsp; Use the ssh-kegen command in a terminal as follows:

    ssh-keygen -t rsa -C your.email@address.com
    
Accepting all the defaults will work correctly, optionally adding a password.&nbsp; A new file will be created in your home directory which holds your public key `~/.ssh/id_rsa.pub`.

To add the generated key to your assembla.com account, open assembla.com in your browser and login.  Once logged in you will be on the `My Start Page`.  Select the `Start` > `Profile` tab to edit your account settings.  Further down the profile page is a section called Git Settings, click the link called `Manage your public SSH keys`.  

You can cut-n-paste the contents of the `~/.ssh/id_rsa.pub` file or browse to the file from the web page and add your public key file that was generated with the ssh-keygen command.

Once you have added your public key to your account you can push changes to any of the git repositories you have created or been given write access to at assembla.com.

# Installing a client to access the code repository (git)

Install the package git-core using your favourite package manager or using the following command:

    apt-get install git-core**</pre>

# Configure a git client

You should introduce yourself to git by configuring a git user name and email address.&nbsp; This information is used when you push changes back to the central git repository, so you changes have identity.

    git config --global user.name "John Stevenson"
    git config --global user.email john@jr0cket.com

# Create a local git repository (only for a new git repository)

At present the repository on the LSUG-dojo workspace on assembla.com is empty.&nbsp; To add files to the assembla.com git repository we first create a local git repository using the following commands:

    mkdir lsug-dojo
    cd lsug-dojo
    git init

A README file was created in the top level so that there was something to commit.

> Tip: Using a README file is very useful as the contents of this file is displayed when browsing the source code on the assembla.com website.

Lets add the README file (and any other files/folders we could have created) to the local repository and commit that added file to the local repository with a suitable message representing the change we are making.

    git add .
    git commit -m "Initialising LSUG-dojo Git repository on Assembla"

# Push changes to LSUG-dojo git repository

To push to the locally created files to the git repository on assembla.com, a push command is needed.&nbsp; However, the local repository first needs to be told about the remote git repository.

Lets go ahead and add the changes locally and commit to the master on assembla.com with the following two commands:

    git remote add origin git@git.assembla.com:lsug-dojo.git
    git push origin master

The git push command will submit all the changes committed to the local git repository to the lsug-dojo git reposiory on assembla.com, using the branch called master.&nbsp; 

# Public read-only access to the git repository

The repository on assembla is open for anyone to read and download the source code.&nbsp; The code can be browsed via the LSUG-dojo site on assembla or downloaded locally using `git clone`

    git clone git://git.assembla.com/lsug-dojo.git

This command will create a folder called lsug-dojo in the current folder path.&nbsp; The lsug-dojo contains a complete copy of the current version of all the dojo code.

# Committer access to the git repository

In order to push changes to the lsug-dojo git repository, you must be assigned that priveleged by the owner of the lsug-dojo assembla.com workspace.

Once you have been granted write access to the git repository, you have registered your private key with assembla (as detailed at the start of this article).

You must also clone the assembla.com repository using the private address as follows

    git clone git@git.assembla.com:lsug-dojo.git

Using the private address of the lsug-dojo git repository allows the use of a secure shell connection to push changes to the lsug-dojo repository.

Pushes to git for the dojo project code will be done on the evening of the dojo by one of the organisers of the dojo.

# Post dojo updates

After a dojo has finished, the code will be added to the git repository on assembla.com.

Lets check the status of git, this will tell us what changed files we have in our project structure

    git status

The  git status is tell us that we need to add the code changes to the local  copy of our git repository, then we can decide to commit those changes  to the master git repository on assembla.com.

Here is an example output from git status after the second scala dojo:

```
git status
# On branch master
# Changed but not updated:
#   (use "git add <file>..." to update what will be committed)
#   (use "git checkout -- <file>..." to discard changes in working directory)
#
# modified:   minesweeper-dojo/.idea/workspace.xml
# modified:   minesweeper-dojo/minesweeper-dojo.iml
# modified:   minesweeper-dojo/src/main/scala/com/assembla/lsug/dojo/minesweeper/Board.scala
# modified:   minesweeper-dojo/src/test/scala/com/assembla/lsug/dojo/minesweeper/BoardReaderTest.scala
#
# Untracked files:
#   (use "git add <file>..." to include in what will be committed)
#
# minesweeper-dojo/target/
no changes added to commit (use "git add" and/or "git commit -a")
```

# Add the files to the local repository

If we know that there are new files created from the dojo or if you are not sure, run the following command:

    git add minesweeper-dojo

This will tell git to add any new files within the minesweeper-dojo folder to the repository when you do a commit.

To check what is to be added, run `git status` again

# Excluding files and folders

To exclude certain files and folders, create a file called .gitignore in the project folder (at the same level as the `.git` folder).

Add folder names with a trailing / and include the relative folder path. The current `.gitignore` file contains the following lines:

``` .gitignore
minesweeper-dojo/target/
minesweeper-dojo/.idea/dictionaries/johnny.xml
```

# Reset what you want to add to git

If you are not happy with the files that have been addded, you can tell git to forget them with the following command:

    git reset HEAD .

# Commit the changes locally

Version the changed files from the dojo by committing them to the local repository, using a suitable commit message that represents the change or major activity from the dojo.&nbsp; The commit message defined here is used when we push the local changes to the public assembla.com repository.

    git commit -m "suitable commit message"

# Push the changes to assembla.com

Now that the file changes have been committed locally, we can share those changes publicly by pushing the master branch that holds the changes to the origin - the assembla.com git repository.

    git push origin master


# In Summary

Using Git is an easy way for developers to collaborate and share code during a coding dojo.  Online tools like Assembla.com allows any developer, even outside of the London Scala community, to take a look at what was created all any and all our dojo's.

Thank you.
[@jr0cket](https://twitter.com/jr0cket)

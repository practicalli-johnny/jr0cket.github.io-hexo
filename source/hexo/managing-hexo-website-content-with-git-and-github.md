title: Managing Hexo website content with Git and Github
date: 2014-07-02 21:37:14
---

{% img img-thumbnail /images/github-logo.png %}

In this section we will create a local git repository manage changes to the important files and directories in your Hexo website project.  Those changes will be copied to a repository on Github, becoming an exact copy in the cloud.

> Whist this step is optional it provides many benefits. Its a good way to back up your content to somewhere relatively safe (in terms of your laptop going bang).  Using a distributed version control system like Github also makes it really easy to collaborate with others, allowing them to submit content for new articles and corrections for existing content.

So lets set up your Hexo website content under version control using Git and Github.

# Install Git

Git is available from the [Git website](http://git-scm.com).  Download and install the approprate version for your operating system.

> On Ubuntu systems you can install Git using the package manager `sudo apt-get install git`

Once installed you can test git is working using the following command in a terminal:

    git --version

## Tell Git your name 

To understand who as created which change in Git, you should configure your name and email address (your email address should be the one you use for Github in the next step)

    git config --global user.name "YOUR NAME"
    git config --global user.email "YOUR EMAIL ADDRESS"

# Create an account on Github

Visit the [Gihub website](https://github.com) in your browser and follow the steps to create an account (or login if you already have an account).

Add your public key to your Github account, see the [Github Help pages on SSH Keys](https://help.github.com/articles/generating-ssh-keys).


# Versioning your Hexo project

Now we are going to create a Git repository within your Hexo project. The repository will contain the full history of every change you add to git.

Inside your hexo-website folder, use the command

    git init 

## Add the important files to you Git repository 

Add the important files to Git and then commit those files as the first change:

    git add _config.yml packages.json .gitignore scaffolds/*.md 
    git commit -m "Adding a new Hexo website"


# Create a Repository on Github

Sign into your account on [Github](https://github.com) and create a new repository

{% img img-code /images/hexo-github-repository-create.png %}

Once your new repository has been created, Github shows you the details for accessing it.

{% img img-code /images/hexo-github-repository-details.png %}

Add this new repository to your local git repository

    git remote add origin git@github.com:jr0cket/jr0cket.github.io-hexo.git

Now copy all your changes that have been commited in your local Git repository to the Github repository.

    git push origin master 

> By convention, the name origin is used to refer to the canonical Git repository for the project.  Origin is only an alias for the repository URL, so you can use what ever name you like for the alias so long as its unique for your local repository and you use the same name for `git remote add` and `git push`.


# Adding more changes

When you make more changes to your project, add those changes to your local Git repository and then send them to Github.

    git add filename
    git commit -m "description of the change"
    git push origin master

# In case of disaster

Should the worst happen - your laptop goes bang or your project is accidently deleted - you can easily recover all the changes you pushed to Github with a single command:

    git clone origin git@github.com:jr0cket/jr0cket.github.io-hexo.git


[Back to Hexo overview](index.html) | [Next: Configure your Hexo website](configure-your-hexo-website.html)


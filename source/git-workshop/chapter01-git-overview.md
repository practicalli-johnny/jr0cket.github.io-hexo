# <a id="#chapter1">Git overview</a>

Git is a very powerful tool for managing the changes you make as you develop source code for your software projects.  Typically those changes tracked are the ones made to source code and configuration files.  Git understands how to merge text files together, allowing you to pull in changes from others.  It also helps you compare changes in different versions of text files using the diff tool.

You can also manage binary files such as images and propriatory document formats, although git does not typically come with tools that help you merge or compare differences.

Before the creation of Git (and Mercurial, Bazar and a few others), most versioning tools for source code used what is called a central model.  Tools like CVS and SVN manage code changes in a single central server, shared across teams and the whole company.  When developers work on code they only get a copy of current code locally on their development machine.  To actually do any commits, to version the code, then they have to connect with the server.  When looking at history and any other activitiy, developers have to communicate with the central server.  If this server is off line or slow, then this can lead to problems working effectively together as a team.

Git uses a distributed approach to managing changes (as does bazar & mercurial).  This approach may seema little more complicated at first, but adds far more control and visiblity to your projects.

A distributed model means that everyone involved gets a complete copy of the project repository.  It is still common to have a shared repository that holds all the code (e.g. on Github), although this can easily be changed and may evolve over time.

Using Git, developers create a copy of a project repository on their development machine, this is called *cloning*.  This creates a local copy of the repository along with all the files managed by git in your project.  As you have a local repository, all the code changes that  have ever been made are right there giving you a full history of the project.

One of the benefits of git therefore is to be able to constantly commit changes, regardless of if you are connected to a shared repository.  You commit all your changes locally first (even if you are connected) and then when ready you can push your changes to a shared repository.

It is common to have a common shared repository that is seen as the canonical version of the code for a project.  The core members of the project team, refered to as *committers* have direct access to update this shared repository.  Anyone with access to the project repository can take a copy (clone).

Should you wish to work on the project you can create your own copy, called a fork.  Your fork is your own exact copy of the oringinal repository, including all the history.  As this is your repository, you can commit changes directly.

Should you wish to submit your chages back to the original project, you can create a pull request from your fork.  A pull request is a message and one or more commits that are sent to the original project team, inviting them to pull in the changes from your forked repository.


[Back to top...](#top) | [Next: Choose your git client](chapter02-choose-your-git-client.html) | [Back to Workshop home...](index.html)

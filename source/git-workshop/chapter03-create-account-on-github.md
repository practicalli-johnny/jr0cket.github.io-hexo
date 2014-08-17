<link href="index.css" rel="stylesheet" type="text/css">

# <a id="top">Create an account on Github</a>

Git hub adds extra collaboration features over git, providing a *social coding* service which is an excellent resource for working on projects as a team and running open source projects.  Anyone can get a copy of code (clone) in your public repositories, whether or not they have an account on Github.  You don't need any access permissions to do so.

If you want to work on a project where you are not a collaborator, you can fork a repository and either develop using that new repository yourself or create pull requests that are sent to the collaborators of the original project.

* Forking a repository - creates a new github repositiory for you from a github repository owned by another person or organisation. You have full commit access to this new repository, because its owned by you.

* Creating a pull request - sends a message to the committers on the original project (the one you forked), inviting them to pull your changes into their project.

To create a free account on Github, go to [www.github.com](https://www.github.com) and follow the instructions.


## Make committing code easier by upload your public key

Any time you send code to github it is done over a secure connection and therefore you have to identify yourself.  This means you either have to enter your username / password frequently or add those details to your IDE (eg. Eclipse, Intellij, Netbeans, etc.), which may save them as plan text.

Rather than use your username and password, pubic key encryption can be used to identify yourself to github (and other services like [heroku](http://www.heroku.com)).  Once you have added the public key to github, every time you connect to github then that key is used to automatically identify you.

You can create and add your public key using the [excellent instructions on the gthub website](https://help.github.com/articles/generating-ssh-keys)

If you have already set up Heroku Toolbelt and used the command *heroku login* then you may already have a public key.  The key that heroku created can also be used for github, assuming you have used the same email address for both accounts.

[Back to top...](#top) | [Next: Idenify yourself to Git](chapter04-identify-yourself-to-git.html) | [Workshop homepage](index.html)

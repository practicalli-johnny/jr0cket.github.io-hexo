title: Hey Prezto - Zsh for Command Line heaven
date: 2013-09-02 16:11:00
categories: dev-tools
tags:
- zsh
---

{% img img-thumbnail http://3.bp.blogspot.com/-OCKvFRcGPLk/UTUY7NXSS6I/AAAAAAAAJI0/RJT6XMB05I4/s1600/Zshell-silver-rotating.gif %}

Using the command line is a powerful and quick way of doing many developer tasks.  The [command line shell](http://en.wikipedia.org/wiki/Shell_(computing)) for Linux & MacOSX is a whole world apart from the very basic experience of DOS. Zsh (Z Shell) makes the Linux & MacOSX shell experience even better.

I learnt to use the command line with bash, the default Linux shell.  Although as soon as you play with zsh for a few minutes, you quickly get hooked.  zsh gives you [lots of features](http://www.acm.uiuc.edu/workshops/zsh/why.html), including:

* auto-completion on steroids
* command relative completions
* navigable completions list
* amazingly fast completions
* auto corrections for when your fingers slip
* custom prompts, a right hand prompt and themes
* shared history over all terminals
* history sub-string search

You can add libraries to bash and configure it to do these things as well, although I havent seen an projects to help you quickly do so.

Still not convinced, then take a look at Brendan Rapps presentation "[Why Zsh is cooler than your shell](http://www.slideshare.net/jaguardesignstudio/why-zsh-is-cooler-than-your-shell-16194692)"

# Get going with Zsh

You can just install zsh and configure it yourself.  On the Mac, Zsh is installed by default.  On Ubuntu its available in the software center or via the command line:

    sudo apt-get install zsh

Configuring Zsh yourself would take a bit of discovery, so I prefer to use something a bit more out of the box.  Luckily there are two projects to choose from that configure everything for you.

# [oh-my-zsh](https://github.com/robbyrussell/oh-my-zsh)

This is a popular project that provides an out of the box zsh setup and its really easy to use.  However, something is making it a little slow when I tried it on the MacBook Pro and Linux.  Comments around this project suggest its written in more of a bash way than zsh, so that may be the reason for a performance slow down.

After a few days I decided to remove oh-my-zsh and try an alternative project.

# [Prezto](https://github.com/sorin-ionescu/prezto)

Prezto has been rewritten by the author who wanted to achieve a good zsh setup by ensuring all the scripts are making use of zsh syntax.  It has a few more steps to install but should only take a few minutes extra.

## Installing Prezto

In the root of your home account, clone the prezto github project using any git client.

    git clone --recursive https://github.com/sorin-ionescu/prezto.git "${ZDOTDIR:-$HOME}/.zprezto"

> If you don't have a Git client either download it from the [git-scm website](http://git-scm.com/) or use the Ubuntu package manager to install the package called git (`sudo apt-get install git`).

All prezto files are contained within a foloder called `.zprestorc` in the root of your home folder.  In order to use Prezto configuration for zsh, symlinks are used.

> The project gives you a script to run although this didn't work for me and I just created the symlinks manually.

## Create the symlinks manually

In the root of your home folder, create the sym-links using the Unix symbolic link command as follows:

    ln -s ~/.zprezto/runcoms/zlogin ~/.zlogin
    ln -s ~/.zprezto/runcoms/zlogout ~/.zlogout
    ln -s ~/.zprezto/runcoms/zpreztorc ~/.zpreztorc
    ln -s ~/.zprezto/runcoms/zprofile ~/.zprofile
    ln -s ~/.zprezto/runcoms/zshenv ~/.zshenv
    ln -s ~/.zprezto/runcoms/zshrc ~/.zshrc

Check that the links have all been created successfully.  Type the command ls -la and you should see the following in your terminal (although possibly without colour)

{% img img-code http://3.bp.blogspot.com/-mdwsHb5FkGg/UiSqw8hI1mI/AAAAAAAAK7I/TYPgGmWWuBA/s1600/zsh-symlinks.png %}

zprezto uses a series of symlinks to configure zsh with lots of nice defaults

> I have been thinking of changing the use of sym-links and just have the specific files include the Prezto files first, then add any customisations required.  This would help to keep my changes in place when I updated Prezto.

# Run zsh

Now you have zsh configured with prezto, its time to try it out.  Open a terminal window and run zsh using the command:

    zsh

Set zsh as the default shell

To set zsh as our default shell then run the change shell (chsh) command:

    chsh -s /usr/bin/zsh

On Ubuntu, this didn’t seem to work.  I also had to configure Gnome Terminal to run zsh as a custom command.

{% img img-code http://4.bp.blogspot.com/-t5Pv8i_1gCI/UTUV_FUoinI/AAAAAAAAJIs/-zIeS__lNeo/s1600/terminal-zsh-custom-command.png %}

Now when I open a new terminal window or tab, the command line is running Zsh.

# Showing Git branch by switching on zsh modules

Several of the prezto zsh modules are switched on by default, however Git is not one of them.  If you want to see the current branch you are working on in Git then add the git module to the zprezto configuration.

Edit the file `~/.zprezto`

Find the section in the file that defined modules to load and add a line with the git module.  Here is what that section would look like once you have edited it.

    # Set the Prezto modules to load (browse modules).
    # The order matters.
    zstyle ':prezto:load' pmodule \
      'environment' \
      'terminal' \
      'editor' \
      'history' \
      'directory' \
      'spectrum' \
      'utility' \
      'completion' \
      'git' \
      'archive' \
      'prompt'


# Creating my own prezto theme

The default sorin them is okay, but takes up a bit much room on the prompt than I like.

{% img img-code http://3.bp.blogspot.com/-hi59uLe-cTE/UTUa41BodSI/AAAAAAAAJI8/ZoDa9OxOmvY/s1600/zpresto-default-theme.png %}

I created my own theme as a slight variation from the default sorin theme.  I removed >>> characters used to separate the prompt from commands as they seemed largely unnecessary.  As I only use git then I didnt feel the need to specify the version control tool used (eg. git, mercurial).  Finally, I changed the colours round a little.

I kept the right hand prompt as part of my theme. Its a quick way to show the status of any changes in your local git repository.
{% img img-code http://1.bp.blogspot.com/-Q7quGwje_w4/UTUoVbZZRmI/AAAAAAAAJJU/f4udzvNaOnM/s1600/zprezto-prompt-jr0cket-context-specific.png %}

The prompt shows the current folder name, with any parent folders abbreviated to their initial.  The path up to and including the home folder is represented by `~`.

When you enter a folder managed by git, then the right hand prompt kicks in and shows icons representing the current git status.  Whilst in the folder you can see if you have changes that untracked, deleted or stage.  You can easily tell if you are behind or ahead of the default remote repository.  You can also see if you have some changes stashed away.

My zsh theme is available as part of my [dot-files-ubuntu](https://github.com/jr0cket/dot-files-ubuntu) or [dot-files-macosx](https://github.com/jr0cket/dot-files-macosx) repositories.

# Summary

Whist [oh-my-zsh](https://github.com/robbyrussell/oh-my-zsh) is really simple to use, the [Prezto](https://github.com/sorin-ionescu/prezto) project seems to have maintainters with greater experience of zsh.

On Ubuntu I am using prezto and although it is a bit more involved to understand at first, it runs really really fast.  The only thing I wanted to change with prezto was the theme, so not really that much to learn.

Everything that I was doing with oh-my-zsh seems to work in Prezto without adding in extra plugins to the Zsh configuration.

So although oh-my-zsh is a great project, I'd recommend using Prezto to have a great Zsh experience.  Take a look at my dotfiles on github ([dot-files-ubuntu](https://github.com/jr0cket/dot-files-ubuntu) or [dot-files-macosx](https://github.com/jr0cket/dot-files-macosx)) to see how I created a custom theme.

Thank you.
[@jr0cket](https://twitter.com/jr0cket)

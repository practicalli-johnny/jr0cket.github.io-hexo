title: beautiful terminalation - ohmyzsh on ubuntu
date: 2017-08-19 13:58:08
categories: ubuntu
tags:
- zsh
- ohmyzsh
- ubuntu
- powerline
---

I frequently use the command line because of its speed and am using [ohmyzsh](http://ohmyz.sh/) to make the experience more valuable and enjoyable.  I configure ohmyzsh to use the [powerlevel9k theme](https://github.com/bhilburn/powerlevel9k) which provides lots of useful information as well as looking fancy.

![Ohmyzsh with powerlevel9k theme in action](/images/ohmyzsh-powerlevel9k-theme-animated.gif)

> We are more connected to the work we do if its an enjoyable experience.

Read on for details on how to configure Ubuntu with zsh, ohmyzsh and powerlevel9k theme.

<!-- more -->

## Install zsh

Ubuntu has a package for `zsh` so its easy to install

```bash
sudo apt install zsh
```

You could try this new shell by typing `zsh` in the terminal window, however its not going to be as nice without some configuration first.  So lets add that next.

## Install ohmyzsh

Oh-My-Zsh is an open source, community-driven framework for managing your ZSH configuration. It comes bundled with a ton of helpful functions, helpers, plugins and lots of themes to make your command line look fancy!

Install `ohmyzsh` with either wget or curl.  I prefer wget on Ubuntu as its installed by default

```bash
sh -c "$(wget https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh -O -)"
```

See the [ohmyzsh website](https://github.com/robbyrussell/oh-my-zsh) for alternative installation information.


## Install the powerlevel9k theme

Powerlevel9k is a theme for ZSH which is easy to customise and feature rich.  The theme works for your own custom zsh setup as well as ohmyzsh, prezto and other configuration.


Clone the powerlevel9k theme into the existing `ohmyzsh` project

```bash
git clone https://github.com/bhilburn/powerlevel9k.git ~/.oh-my-zsh/custom/themes/powerlevel9k
```

Edit the `./zshrc` file and set the theme to powerlevel9k

```
ZSH_THEME="powerlevel9k/powerlevel9k"
```

> Ensure that there is only one theme set with this value.


## Installing Powerline fonts

The powerlevel9k theme uses Powerline Fonts so we need to install them too.

There are several powerline packages in the ubuntu archives, so either install the powerline fonts or use the powerline meta-package to include powerline support for python too.

```bash
## just the fonts
sudo apt install fonts-powerline

## or use the meta-package for python support too
sudo apt install powerline
```

> To find the packages I simply searched the Ubuntu archives using the command `apt-cache search --names-only powerline`


## Set your default shell

Once you are happy with your new setup, you can make zsh the default for the Ubuntu terminal.  Run `terminal` and edit the profile you are using to run zsh:

**Profile Preferences** > **Command** > **Custom command** > `/usr/bin/zsh`

![Ubuntu Terminal - Profile Preferences - Custom Command - Zsh](/images/ubuntu-terminal-profile-preferences-command-zsh.png)

Change the default login shell by running the `chsh` command.  This will prompt you for your login password and then show you the current login shell.  Type `/usr/bin/zsh` if the current shell is not zsh.

![Ubuntu - change login shell to zsh](/images/ubuntu-change-login-shell.png)

## Summary

With a few Ubuntu packages and two cloned repositories you can quickly create an enhanced experience in your command line.

Take a look at [how others have configured the powerlevel9k theme](https://github.com/bhilburn/powerlevel9k/wiki/Show-Off-Your-Config) for there own needs


Thank you.
[@jr0cket](https://twitter.com/jr0cket)

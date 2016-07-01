title: git 2.9 on ubuntu 16.04
date: 2016-06-18 15:52:09
categories: ubuntu
tags:
- ubuntu
- git
---

{% img img-thumbnail /images/git-logo.png %}

[Git version 2.9 has been released](https://github.com/git/git/blob/master/Documentation/RelNotes/2.9.0.txt) and it brings some [new features and performance benefits](https://github.com/blog/2188-git-2-9-has-been-released) when using git submodules.

Here is how to install Git version 2.9 on the latest release of Ubuntu (16.04)

<!-- more-->

## Installing on Ubuntu

Ubuntu 16.04 comes with Git 2.7.x, which is a little old now.  As versions 2.8 & 2.9 are not part of the Ubuntu repositories, you need to add the git-core personal package archive.

Open up a terminal and run the following commands, supplying your password when prompted.

```
sudo add-apt-repository ppa:git-core/ppa
sudo apt-get update
sudo apt-get install git
```

To check the new version of Git is working, use the following command:

```
git --version
```

## Whats new?

Rather than copy everything here, there is a very good [overview of the Git 2.9 release](https://github.com/blog/2188-git-2-9-has-been-released) on the [Github blog](https://github.com/blog/).  Or take a look at the in-depth [release notes](https://github.com/git/git/blob/master/Documentation/RelNotes/2.9.0.txt).


Thank you.
[@jr0cket](https://twitter.com/jr0cket)

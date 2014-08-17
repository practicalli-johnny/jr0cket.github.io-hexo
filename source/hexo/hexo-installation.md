title: Hexo Installation 
date: 2014-07-10 17:01:00
---

As Hexo runs on NodeJS then you need to have a recent version of nodejs installed.

> Node can be installed via your operating system package manager or as binaries from [nodejs.org](http://nodejs.org).  The Node package manager is part of the node install.  If you install node via your package manager or in a system path eg, `/usr/local` or `/opt` then you will need to use the `sudo` command with any `npm install` command.

Once node is installed, use the node package manager to install Hexo

    npm install -g hexo 

> Using the `-g` option tells the node package manager to install Hexo globally.  If nodejs is installed in the operating system path, you will need to use the `sudo` command 

# Testing the Installation

You can test Hexo is installed correctly by running the command:

    hexo -v

The output of this command will be similar to:

    hexo: 2.7.1
    os: Linux 3.11.0-23-generic linux x64
    http_parser: 1.0
    node: 0.10.26
    v8: 3.14.5.9
    ares: 1.9.0-DEV
    uv: 0.10.25
    zlib: 1.2.3
    modules: 11
    openssl: 1.0.1e

# Udating Hexo 

Hexo is easily updated using the node package manager, using the command

    npm update hexo 

# Uninstalling Hexo 

Should you wish to completely remove Hexo, you again use the node package manager as follows:

    npm uninstall hexo 


[Back to Hexo overview](index.html) | [Next: Creating a Hexo project](creating-a-hexo-website.html)


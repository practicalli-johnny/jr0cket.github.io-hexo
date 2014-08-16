title: Password protected SSH key for Github for Mac & Linux
date: 2012-12-31 15:57:00
categories: dev-tools
tags: 
- github
- heroku
- security 
---

{% img img-thumbnail http://2.bp.blogspot.com/-vIpCWBThzsw/T8ZKPxPTC8I/AAAAAAAAIHU/di86sKgUYA8/s1600/public-private-keys.jpg %} 

Secure Shell (SSH) is an invaluable tool to help developers manage code and data over different computers and services, eg. [Github](http://github.com), [Heroku](http://www.heroku.com).  By creating a public/private key it also means you dont have to enter a username & password each time you use the service.  Ideally you should create a public/private key using a long passphrase, so that is what I will cover here.

<!-- more --> 

## Why use a secure key?

To make using SSH a great experience to use and yet keeping it secure as possible requires you to set up an public / private key combination that is protected by a long pass-phrase.  Specifically you are protecting your private key as you distribute your public key (which is why its called public).  Imagine the pass-phrase as a kind of long password, which you will add to something called a keychain on your laptop so you only have to enter this long password once.

{% img img-topic http://1.bp.blogspot.com/-qlVcL6zWbjY/TzFMw8PPiGI/AAAAAAAAEbs/-Ozv0X_6mrQ/s1600/github-logo.png %}

## I don't want to keep typing my long password on every commit?

Of course not, that would be a real pain.

When using a password protected SSH key with Mac OSX and Linux you can add your SSH key password to the keychain (keyring in Linux, but its the same thing) of your login account.

When you first connect to github using your newly added key you will be prompted with a dialog box to add the password for your SSH key to your keychain.  Enter the password for your keychain in this prompt, it should be the same as your computer login password (unless you specifically changed it).

## Creating a password protected SSH key

Creating an SSH key pair with a long pass-phrase is just the same process as that without, except you obviously specify the long password.

In the following example, I am specifying the email I used for the Github account I own, using the `-C` option for `ssh-keygen`.

I am also using a custom file name.  In doing so, I need to provide the full path to the file or otherwise ssh-keygen fails to create the file.  It seems that even the `~/` shortcut to your home folder also fails.

As I am using a custom name for the keys, then I will need specific a host configuration before I am done.

{% img img-code http://3.bp.blogspot.com/-Y7vVzBfsOZE/UOG0phBIZHI/AAAAAAAAI2w/doqqeqnO3fQ/s1600/github-ssh-key-generation-secure.png %}

## Adding a Host configuration

If your public key is called id_rsa.pub then you should not need a host configuration.  As I am using a custom name to generate the SSH keys, I need to add a host definition to my SSH configuration.  Its pretty easy to add a new definition, simply edit the ~/.ssh/config file and add a definition as follows

{% img img-code http://2.bp.blogspot.com/-Wt1uj7Hxnec/UKaKa29sKwI/AAAAAAAAIjA/XtmLKuvJQ-g/s1600/ssh-host-config-github-secure.png %}

## Adding Keys - a bad Developer experience

{% img img-code http://3.bp.blogspot.com/-0xWwyDAsFGU/UKaiV_bcAWI/AAAAAAAAIjY/iMdnVj8lVNQ/s1600/github-profile-edit.png %}

The adding of keys to your Github account is a very poor experience for the developer, as it requires a cut-n-paste rather than allowing you to upload your key file.

Adding keys to **[Heroku](https://devcenter.heroku.com/articles/keys)** is much nicer, they have a **[toolbelt](https://toolbelt.heroku.com/)** that automatically detects your public key file and upload it. 

I had a few problems when copy/pasting my key from the editors that come with the Mac, until I found reference to the command `pbcopy`.

Open up a terminal and enter the following command to copy your public key into the Mac's clipboard.  Then simply paste the key into the Github webpage for adding a new key. 

    pbcopy < ~/.ssh/id_rsa.pub

Bitbucket is not much better, although at least they tell you about pbcopy in the documentation for adding a key.  When I used Assembla.com, at least you could upload your key public key as a file.

Once you have uploaded your public key, don't forget to give it a quick test to make sure its all working.  Using the command line, use the ssh command to connect to github

    ssh -T git@github.com

{% img img-code http://3.bp.blogspot.com/-pYOW0NB6RfA/UKaiX5iv1oI/AAAAAAAAIjg/SZBS1NMG11c/s1600/github-testing-successful.png %}

This command will use your SSH key to connect to Github and show you if you have successfully set up your key for your account on your Mac.  Unlike normal SSH access, you cant actually do anything once you connect.

Thank you.

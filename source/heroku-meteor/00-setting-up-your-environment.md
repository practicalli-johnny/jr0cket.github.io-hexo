# <a id="top">Setting up your Heroku & application development environment</a>

  Before you start developing your application, you will need to have the following:
  
  * An Internet connection
  * An Heroku account
  * The Heroku toolbelt (`heroku`)
  * **A credit card** (for using addons - you will not be charged)
  * A public key added to heroku (`heroku keys`)
  * The Meteor framework (`meteor`)
  * A text editor (anything will do)

  This section will help you set up any of the above requirements for this workshop.  
  
> Note: these requirements are specific to this workshop.  To use Heroku outside of this workshop, the minimum you need is an Heroku account, a Git client and an Internet client. 

## Create an Heroku Account (if you dont already have one)

  You can create a free account at the Heroku website.  You need an account in order to deploy and manage the applications on Heroku.

  1. In your browser navigate to: [https://heroku.com/signup](https://heroku.com/signup)
  2. Enter your email address
  3. Select `Sign Up`
  4. Check your email for a message from Heroku and navigate to the verification page given in that message.
  5. On the verification page, enter a suitable password for your account


## Installing the Heroku Toolbelt

  The Heroku toolbelt is a command line application for creating and managing your applications on Heroku.  Its a really useful tool.  The toolbelt also contains a Git client, although you can use your own Git client if you prefer.
  
  When you created your account, the Heroku website directs you to download the Heroku toolbelt.  It is also available from the [Heroku toolbelt website](http://toolbelt.heroku.com) if you do not have it on your development machine.
  
  Install the Heroku toolbelt version for your operating system and test it is installed by using the following command
  
    heroku
    
  If the Heroku toolbelt is correctly installed, you will see a list of the Heroku tasks you can carry out.

## Ensure you have the latest version of the Toolbelt

  If you already had the toolbelt installed before this workshop, please update it to make sure it is the latest version.
  
    heroku update

> On some operating systems such as Debian/Ubuntu, heroku can be updated using their package management tool, eg sudo apt-get install heroku*


## Setting up secure access to Heroku (public key)
  
  When you deploy your application code to Heroku via Git, a secure shell (SSH) connection is used.  This ensures your code is transfered securly and allows Heroku to confirm you are authorised to access that specific application on Heroku.  This SSH connection requires you to add a public key to your Heroku account.
  
  The first time you work with Heroku you can use the following command to create a public key for you or upload any existing public key you may have:
  
    heroku login

  To check what keys have been added to your Heroku account, using the following command:
  
    heroku keys
  
> Note:  If you already have a key, ensure that it has the email address you used for your heroku account as a comment on the key.*
  
  
  Should you need or want to create your own public key, you can use the following command:
  
    ssh-keygen -t rsa -C "foo@bar.com"

    
  To add a new key to Heroku, use the following command:
  
    heroku keys:add 
    
  If you have only one public key, this command will just add it to heroku without prompting.  If you have more than one pubic key then heroku will prompt you as to which key you want to add.
  
  If you have set up your key and it is being rejected, you may need to [set up a SSH configuration file](http://jr0cket.co.uk/2012/11/managing-multiple-ssh-keys-to-avoid.html).
  

# Setting up Git

  When you install the Heroku toolbelt it includes a Git client.  You can also use any other git client you want, either command line or graphical tool.
  
  You do need to identify yourself to Git before carrying out any commits to your local repository.  You must specify git user.email and optionally specify git user.name.
  
  To add your git name and email, either edit the `~/.gitconfig` file or run the following two commands:

    git config --global user.name "your name"
    git config --global user.email "your.name@domain.com"

  To check what has already been added to Git (some gui clients add information), you can list all the current configuration entries:

    git config --list

  If you are still finding your way with Git, take a look at the seperate Git and Github tutorial](http://git-and-github-workshop.herokuapp.com/).
  

## Download & install the Meteor framework

### Linux and MacOSX
Run the following command in a terminal to download and install Meteor.  

    curl https://install.meteor.com | /bin/sh

> Note: You will need to supply your operating system password when Meteor is installing as it is placed in a protected part of the file system.

  
### Microsoft Windows

A specific Microsoft windows download is available at: [http://win.meteor.com/].


### Test Meteor framework is working

  Test meteor is configured correctly by running the following command:
  
    meteor
    
  Assuming everything went okay, you are now ready to create your first JavaScript application using Meteor.

[Next](01-getting-started-with-your-app.html)
[Back to top...](#top)
[Back to Workshop home](index.html)


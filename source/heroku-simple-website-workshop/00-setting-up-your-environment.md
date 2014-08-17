# <a id="top">Setting up your Heroku & application development environment</a>

Lets start by setting up your environment.  To do so you will need an Internet connect.

By the end of this chapter you will have:

  * An Heroku account
  * The Heroku toolbelt (`heroku` and `git`)
  * A public key added to heroku (`heroku keys`)
  * Nodejs & Node package mangager (optional extra)

> Note: these requirements are specific to this workshop.  To use Heroku outside of this workshop, the minimum you need is an Heroku account, a Git client and an Internet client. 

## Create an Heroku Account (if you dont already have one)

  You can create a free account at the Heroku website.  You need an account in order to deploy and manage the applications on Heroku.

  1. In your browser navigate to: [www.heroku.com](https://heroku.com/) and click the **Sign Up button**.
  2. Enter your email address
  3. Select `Sign Up`
  4. Check your email for a message from Heroku and click the link provided to verify you account.
  5. On the verification page, enter a suitable password for your account (8 characters or more, a combination of letters & numbers)


## Installing the Heroku Toolbelt

  Install the [Heroku toolbelt](http://toolbelt.heroku.com) on your computer.

  The Heroku toolbelt is a command line application for creating and managing your applications on Heroku.  It provides a simple way to manage the applications you have running on Heroku.  You can also use the [Heroku dashboard](https://www.heroku.com/apps)  (no install required) if you do not like using the command line.
  
> The toolbelt also contains a Git client, although you can use your own Git client if you prefer.

## Test the Heroku Toolbelt is working

To test the Heroku toolbelt is working, open a command line terminal and type the following command:
  
    heroku
    
  If the Heroku toolbelt is correctly installed, you will see a list of the Heroku tasks you can carry out.


## Check for the latest version of the Toolbelt

  If you already had the toolbelt installed before this workshop, please update it to make sure it is the latest version.  If you have just installed the Heroku toolbelt then skip this step.
  
    heroku update

> On some operating systems such as Debian/Ubuntu, heroku can be updated using their package management tool, eg sudo apt-get install heroku*


## Setting up secure access to Heroku (public key)
  
  When you deploy your application code to Heroku via Git, a secure shell (SSH) connection is used.  This ensures your code is transfered securly and allows Heroku to confirm you are authorised to access that specific application on Heroku.  This SSH connection requires you to add a public key to your Heroku account.
  
  The first time you work with Heroku you use the toolbelt to create a public key for you or upload any existing public key you may have:
  
    heroku login

  To check what keys have been added to your Heroku account, using the following command:
  
    heroku keys
  
> Note:  If you already have a key, ensure that it has the email address you used for your heroku account as a comment on the key.
  
  
  Should you need or want to create your own public key, you can use the following command:
  
    ssh-keygen -t rsa -C "foo@bar.com"

    
  To add a new key to Heroku, use the following command:
  
    heroku keys:add 
    
  If you have only one public key, this command will just add it to heroku without prompting.  If you have more than one pubic key then heroku will prompt you as to which key you want to add.
  
  If you have set up your key and it is being rejected, you may need to [set up a SSH configuration file](http://jr0cket.co.uk/2012/11/managing-multiple-ssh-keys-to-avoid.html).
  

# Setting up Git

  When you install the Heroku toolbelt it includes a Git client.  You can also use any other git client you want, either command line or graphical tool.
  
  You should identify yourself to Git before carrying out any commits to your local repository.  To do this you specify your git user.email user.name.
  
  To add your git name and email, either edit the `~/.gitconfig` file or run the following two commands:

    git config --global user.name "your name"
    git config --global user.email "your.name@domain.com"

  To check what has already been added to Git (some gui clients add this information for you), list all the current configuration entries:

    git config --list

  If you are still finding your way with Git and want to learn more then take a look at the [Git workshop](http://jr0cket.co.uk/git-workshop).


[Next](01-getting-started-with-your-app.html)
[Back to top...](#top)
[Back to Workshop home](index.html)


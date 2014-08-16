title: Sublime Text on Ubuntu
date: 2013-09-03 12:32:00
categories: dev-tools
tags: 
- sublimetext
- ubuntu
---

{% img img-thumbnail http://4.bp.blogspot.com/-zZtRA_8X4Xg/UiXECID9V5I/AAAAAAAAK9s/ucg-FQrgWso/s1600/sublime-text-screenshot.png %}

[Sublime Text](http://www.sublimetext.com/)&nbsp;is a really popular text editor will great language support and a lot of plugin features that are geared towards software developers.

Although I'm usually in Emacs, lots of people have asked me how best to set Sublime Text on Ubuntu, so here is my prefered method.

<!-- more -->

## Download Sublime Text

As Sublime is not part of the Ubuntu package management system (apt-get), it requires a manual download and install. &nbsp;Download the latest version from the [Sublime Text front page](http://www.sublimetext.com/) (it should give you a button specific to the OS you are currently using, i.e. Ubuntu). 

The download will be an archive file like zip but using the Unix commands tar and bzip2.

## Extract the Sublime Text archive

You can extract the whole archive by right-clicking on the file in the file browser (nautilus) and selecting *Extract here*

> You can also double clicking and selecting the Extract button when the archive manager app opens or use the following command in a terminal: tar jvxf "Sublime Text 2.0.2 x64.tar.bz2"

## Install Sublime Text in /opt

I usually place 3rd party software in the folder `/opt` although you could use `/usr/local`.
 
> You just create an apps folder in your own home directory if you use only one login account with Ubuntu.

Create a &nbsp;folder to contain the Sublime Text app using the following command in a terminal: 

    sudo mkdir /opt/sublime

> I am assuming that we will download new versions occasionally and have other apps installed in /opt.

Move the folder and all its contents extracted from the sublime text archive file:

    sudo mv ~/Downloads/Sublime\ Text\ 2 &nbsp;/opt/sublime

Create a symbolic link called `current` that points to the folder you have just moved. 

    ln -s /opt/sublime/Sublime\ Text\ 2 &nbsp;/opt/sublime/current

> If you do upgrade the version of Sublime, simply download the new version and extract it into the /opt/sublime folder, then just delete the symbolic link and create a new one to point to the new folder.

## Add Sublime Text to path to run it from anywhere

Rather than add the sublime folder to the path and making it messy, I create a little bash script that simply calls sublime. &nbsp;Create a new file by launching an editor, use <span style="font-family: Courier New, Courier, monospace;">gksudo</span> if you are launching a graphical editor as the file will be created in the protected part of the file system:

    gksudo gedit /usr/local/bin/sublime

Add the following script to this file that will change to the folder where the sublime binaries live and then run its usual starup script. &nbsp;The `$*` ensures that any parameters such as file names you pass to the script are passed on to the sublime start-up script.

    #!/bin/sh
    cd /opt/sublime/current
    ./sublime_text $* &

Save the file and close the editor.  You have make a new script called sublime on the executable path. &nbsp;However, we still need to give this new script permission to be executed.

Use the following command in a terminal window to make the bash script file executable for every user:

    sudo chmod a+x /usr/local/bin/sublime

You can now call sublime from anywhere and even call it with a file name or path/file name arguments.

Enjoy Sublime text and if you find its not for you there is always Emacs :)

Thank you.
[@jr0cket](https://twitter.com/jr0cket)

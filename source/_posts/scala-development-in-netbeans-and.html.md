title: Scala development in Netbeans and Ubuntu (and MacOSX)
date: 2010-02-25 15:11:00
categories: dev-tools
tags: 
- scala
- netbeans 
---

The Netbeans IDE is a pretty lightweight but easily extensible IDE for different languages that run on the Java Virtual Machine (JVM):

*   Java - native support
*   Groovy - native support
*   Scala - plugin - works with Scala 2.8
*   Clojure - plugin called [enclojure](http://www.enclojure.org/)

This article covers setting up Scala in Netbeans 6.8 in Linux (works on MacOSX too) - includes installing Scala 2.8, [check out the Netbeans guide for Mac and Windows installs and other tips.](http://wiki.netbeans.org/Scala68v1)

<!-- more -->

> Note: If you are feeling adventurous, you can [download a Netbeans nightly build ](http://bits.netbeans.org/dev/nightly/latest/) and add the Scala kit from the netbeans update center.

Any text in green are text or commands for you to enter.

## Download Netbeans

[Get the latest version of netbeans](http://netbeans.org/downloads/index.html) (6.8 at this point in time).  If you are just doing Scala, go for the Java SE download, or Java download if you want Glassfish as well

> You can add all supported technologies easily through the plugin manager, like you use the package manager with Debian/Ubuntu.  Netbeans will only activate a plugin when you first start using it, so even if you install everything its still lightweight.

## Install Netbeans

I create a folder called /opt/netbeans for the installation:

    sudo mkdir /opt/netbeans</span></div>

Run the install file that you downloaded:

    sudo sh ./netbeans-6.8-ml-javase-linux.sh</span></div>

Follow the installer prompts, entering the following path when asked to chose the install folder:

    /opt/netbeans/netbeans-6.8</span></div>

Go and download the latest version of Scala while you wait...

## Download Scala 2.8

[Download the latest Scala-2.8.0 snapshot of the runtime](http://www.scala-lang.org/archives/downloads/distrib/files/nightly/distributions/scala-2.8.0.latest.zip).  Keeping the folder names, extract the zip file using file roller to `/opt/scala/`, so you will have an install in `/opt/scala/scal-2.8.0r20979-bxxxxxx` 

If you dont have permissions to write to `/opt`, run the command 

    sudo mkdir /opt/scala ; sudo chown -R username. /opt/scala 
    
Substitute your operating sytem username above, keeping the full stop to add group access too.

To easily update Scala, create a symbolic link to the newly extracted scala runtime

    sudo ln -s /opt/scala/scala-2.8.0.r20979-b20100225020147 current


## Set the SCALA_HOME environment

For MacOSX, see the [netbeans article for configuring the environment for MacOSX](http://wiki.netbeans.org/MacOSXEnvForApp).

Edit the `/etc/profile` file:

    gksudo gedit /etc/profile</span></div>

Add the following lines at the bottom of the file and save the file

    # Scala runtime environment - latest version
    export SCALA_HOME=/opt/scala/current

Load the settings into your current session by typing the following in your terminal window

    source /etc/profile</span></div>

Test the environment variable is set using the echo command, when run it should print out:

    echo $SCALA_HOME

## Running Scala on the command line

Make the Scala commands executable:

    sudo chmod a+x /opt/scala/current/bin/*</span>

Add Scala to your path by updating your shell resource file (ie. .bashrc or .zshrc)

    # Add Scala to path for login scripts
    export PATH=$PATH:$SCALA_HOME/bin/


## Test Scala works

To test Scala is basically working, run Scala with the version option and you should get output as follows:

    Scala code runner version 2.8.0.r20979-b20100225020147 -- Copyright 2002-2010, LAMP/EPFL

Without updating your executable path you can run:

    $SCALA_HOME/bin/scala -version

If you did update your executable path, then just run:

    scala -version


## Add the Scala Plugin for Netbeans

[Download the Scala Plugin for Netbeans](http://sourceforge.net/projects/erlybird/files/nb-scala/6.8v1.1.0rc1/) (sourceforge page, download the latest zip file ~15MB)

Extract the downloaded zip file to /opt/netbeans/plugins using file-roller (or unzip)

Run the netbeans IDE from the `applications > programming` menu or just running `netbeans` on the command line.

{% img http://2.bp.blogspot.com/_yKz3swsAoNQ/S4akdW_EnwI/AAAAAAAAADo/lN-aFCS8Zko/s1600-h/Netbeans-plugin-manager.png %}

In Netbeans, open the plugins manager by selecting the menu `Tools >Plugins`.

In the plugin manager, select the `Downloaded` tab.

Select the `Add Plugins...` button

Open the `/opt/netbeans/plugins/nb-scala-6.7v1.1.0rc1` directory in the `Add Plugins` diaglog box and select all the `*.nbm` files

{% img http://2.bp.blogspot.com/_yKz3swsAoNQ/S4alja3wxuI/AAAAAAAAADw/9xfLWdE9L_o/s1600-h/Netbeans-plugins-nb-scala.png %}

    "org-netbeans-libs-scala.nbm" 
    "org-netbeans-modules-languages-execution.nbm" 
    "org-netbeans-modules-scala-console.nbm" 
    "org-netbeans-modules-scala-core.nbm" 
    "org-netbeans-modules-scala-debugger-projects.nbm" 
    "org-netbeans-modules-scala-debugger.nbm" 
    "org-netbeans-modules-scala-editor.nbm" 
    "org-netbeans-modules-scala-kit.nbm" 
    "org-netbeans-modules-scala-platform.nbm" 
    "org-netbeans-modules-scala-project.nbm" 
    "org-netbeans-modules-scala-refactoring.nbm" 
    "org-netbeans-modules-scala-stdplatform.nbm" 
    "xtc.nbm"

Select Install to add the plugins to Netbeans and follow the plugins installer wizard.


Important: when configuring the scala plugins, make sure you enter the correct path to the scala install as I have not found a way to change the Scala default environment in the plugin once configured.

## Start a Scala Project in Netbeans

{% img img-code http://4.bp.blogspot.com/_yKz3swsAoNQ/S4am4rbNndI/AAAAAAAAAD4/NrHTQG-LQhc/s1600-h/Netbeans-projects-scala-application.png %} 

To create a new Scala project, open the project wizard by selecting `File > New Project` or use the keyboard shortcut `Ctrl-Shift N`.

From the Categories list, select the Scala folder.

From the project list select `Scala Application`

{% img img-code http://1.bp.blogspot.com/_yKz3swsAoNQ/S4aoM0RFfrI/AAAAAAAAAEA/adDp0l6dDmQ/s1600-h/Netbeans-projects-scala-app-details.png %} 

Enter the details of your Scala application

{% img img-code http://4.bp.blogspot.com/_yKz3swsAoNQ/S4aoqkwdckI/AAAAAAAAAEI/BCgj2fyX0HU/s1600-h/Netbeans-scala-filetypes.png %}

Add Scala traits, objects and classes to the project

Go get functional !!!

[@jr0cket](https://twitter.com/jr0cket)

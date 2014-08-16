title: Java 7 on Mac OSX - OpenJDK and Oracle
date: 2012-09-24 07:06:00
categories: dev-tools
tags: 
- java
- macosx
- openjdk
---

There are many things that make the MacBook pro a nice machine for software developers.  The default version of Java Standard Edition development environment is not one of those things. 

Although Java SE does come pre-installed on most OSX versions, it is the [soon to be unsupported Java 6 version](https://blogs.oracle.com/henrik/entry/java_6_eol_h_h) (unsupported that is without paying Oracle big support fees of course).

Whilst its fairly easy to install Java SE 7 on the Mac, its a little more interesting when it comes to setting it as the default Java runtime environment.  If you also want to try installing OpenJDK 7, then there is a little more discovery to be done when locating the install files.  This article covers the easiest way I found to install Java SE 7 and OpenJDK 7 together.

# Install Java 7

To openjdk or not openjdk, that is the question.  On the Mac there  doesn't seem to be much in it when it comes to ease of installation.   Both Oracle Java SE 7 and OpenJDK 7 come as dmg files for the Mac,  although the OpenJDK files are not as easy to find. 

{% img img-topic http://openjdk.java.net/images/duke-plug.png %}

* **Oracle Java SE 7**: [http://jdk7.java.net/download.html](http://jdk7.java.net/download.html)

* **OpenJDK 7**: [http://code.google.com/p/openjdk-osx-build/](http://code.google.com/p/openjdk-osx-build/)

> There is a website for the [OpenJDK project](http://openjdk.java.net/), although most of the content seems a little dated and unless you are running Linux it provides nothing of interest to help you install OpenJDK on the Mac.  Download the latest versions of Java SE 7 and OpenJDK 7 and open the dmg files to install them.

# Configure the default Java development environment

{% img img-code http://2.bp.blogspot.com/-EefDxGq9ryQ/UF_0CiSUafI/AAAAAAAAIWc/b7zxUylXl28/s1600/macosx-applications-java-preferences.png %} 

OSX allows you to install multiple versions of the Java development environment, a very useful ability especially for testing new versions easily.  In the `Applications > Utilities` folder there is an application called `Java Preferences`.

Running this application lets you manage multiple version of the Java development environment, Java SE.

{% img img-code http://4.bp.blogspot.com/-xV6Z991bVj4/UF_1DIwM0iI/AAAAAAAAIWs/dtT637cbQxY/s1600/macosx-java-preferences-openjdk.png %} 

When a change is made its effects take place immediately, so if you are working in a terminal and change Java versions then you do not need to restart the terminal.

When you have your new versions of Java 7 installed, use the Java Preferences tool to the order around.  If you move an environment to the top of the list it becomes the default choice.

Note that for OpenJDK 7 and Java SE 6 there may be two versions installed.  Use the 64-bit version if you have that option. 

# Testing 

As the changes take effect straight away, you can go to an open terminal and check that Java 7 is the default Java environment using the `java -version` command.

{% img img-code http://4.bp.blogspot.com/-rqKNxf-fz4k/UF_2y7mIAjI/AAAAAAAAIW0/xJW5WxRVpBM/s1600/macosx-java7-version-terminal.png %} 

Over the next few months I will see what development life is like with OpenJDK 7 as the default.  OpenJDK seems to be a newer version than Oracle Java SE, so will have more bug fixes and features - and possibly more bugs.

Using OpenJDK will give me an opportunity to feed back my experiences to the community and if I run into trouble, its easy enough to switch over to Oracle Java SE 7.

Thank you.
[@jr0cket](https://twitter.com/jr0cket)

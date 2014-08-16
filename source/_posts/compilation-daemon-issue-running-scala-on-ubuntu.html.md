title: Compilation daemon issue running Scala on Ubuntu
date: 2010-06-03 10:52:00
categories: dev-tools
tags: 
- scala
- ubuntu
---

When running Scala on Ubuntu Linux, `scala myscript.scala`, if the network configuration in your `/etc/hosts` file does not have a loop back address you can experience the following error:

    Could not connect to compilation daemon.

Edit your `/etc/hosts` file, `gksudo gedit /etc/hosts` and ensure there are the following lines at the top of the file:

    127.0.0.1 localhost
    127.0.0.1 mycomputer

Where _mycompter_ is the name you gave your Ubuntu computer when you installed it.

It would seem that the scala compilation daemon does not pick up the network address when running scripts.  The same problem occurs when there is no network, but I have not found a workaround as yet (except to find a wireless hotspot).

Thank you.
[@jr0cket](https://twitter.com/jr0cket)

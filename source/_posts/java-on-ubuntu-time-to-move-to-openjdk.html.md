title: Java on Ubuntu - time to move to OpenJDK!
date: 2012-02-03 12:27:00
categories: ubuntu
tags: 
- java
- ubuntu
---

Oracle have had many ups and downs with the community over the last few years, although recently I though they seemed to be getting things right.

On the one hand Oracle are supporting [FOSDEM](http://fosdem.org/2012/) but with the other hand are stopping the Sun JDK from being shipped freely by Linux distributions.

Is this simply an aggressive way to move everyone over to the [OpenJDK](http://openjdk.java.net/) platform at a quicker pace?&nbsp; If it is then its a bit of a big stick to use, when you could just use the carrot of new features in OpenJDK 7 &amp; 8.

Now Oracle has retired the ‘distributor license’ which allowed OS vendors to package Sun JDK (August 2011), the security board for Ubuntu  announced that it would be removing Sun JDK package&nbsp;from its ‘_Partner_‘  repository from 16th February 2012.

> “The  Sun JDK packages will remain installed on current systems with no  further security updates. On new systems, it will no longer be possible  to install the packages from the partner archive. “

So if you want a new install of the Sun JDK after February  16th 2012 then you will need to do a manual install by downloading a .bin file from the Oracle website and installing it into `/opt` or `/usr/local/`.  Or you could have a look at the&nbsp; package from one enterprising Ubuntu user, [Martin Wimpress](http://blog.flexion.org/2012/01/16/install-sun-java-6-jre-jdk-from-deb-packages/).

# Moving to OpenJDK

Instead of the fiddling with the Oracle version of Java, you could use this move as a good excuse to test drive your Java applications on OpenJDK which is currently available to install  through the _Ubuntu Software Centre_.

I was concerned about moving over to OpenJDK at first until I realised that I had been using OpenJDK for everything for quite a while anyway.&nbsp; In the last year I have been doing [JIRA](http://www.atlassian.com/software/jira/overview) and [Confluence](http://www.atlassian.com/software/confluence/overview) [plugin development](https://developer.atlassian.com/), using [Netbeans IDE](http://netbeans.org/) and coding with [Scala](http://www.scala-lang.org/) and [Clojure](http://clojure.org/) all on [OpenJDK 1.6](http://openjdk.java.net/) without any issues.&nbsp; So is it time for us to move over to the OpenJDK platform for good?

# In Summary

Its a funny feeling that moving to [OpenJDK](http://openjdk.java.net/) is not only what a huge commercial organisation wants but also a great boost for open source projects in general and of course the OpenJDK project itself.&nbsp; The world has certainly changed in the last few years !!

Thank you.
[@jr0cket](https://twitter.com/jr0cket)

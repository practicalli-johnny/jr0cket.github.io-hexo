title: Faster Clojure REPL startup with Java 9 snapshot
date: 2015-01-03 20:18:13
categories: dev-tools
tags: 
- java 
- clojure
- lighttable
---

{% img img-thumbnail /images/java-logo.png %}

  After upgrading to Java 8, Clojure development seemed faster due to quicker REPL startup times.  So when I saw a snapshot of Java 9 had been released I was hopeful that startup performance would be even faster.

> As Clojure runs on the Java Virtual machine (JVM), each time you start a REPL then you wait for a new JVM to start.  Other than this REPL startup, Clojure feels faster than developing with Java directly.

  Here is how I set up Java 9 Snapshot on my Linux laptop (Ubuntu 14.10), it should be the same for any decent operating system.

<!-- more -->

#### Installing Java 9 Snapshot

> I could have built Java 9 from source and made a `.deb` file of it for a nice install, however the manual install is a lot quicker.
  
  [Download the Java 9 snapshot](https://jdk9.java.net/download/) from the OpenJDK9 website.
  
  I extracted the .tar.gz file into the directory `~/apps/openjdk` and created a symbolic link called `current` that pointed to the extracted directory 

```bash  
    tar zvxf ~/Downloads/jdk-9-ea-bin-b44-linux-x64-23_dec_2014.tar.gz ~/apps/openjdk
    cd ~/apps/openjdk
    ln -s jdk-9-ea-bin-b44-linux-x64-23_dec_2014 current
```

#### Add Java 9 to the system PATH

  I currently have Java 8 installed and its picked up by the alternatives system in Ubuntu, which has java in the `/usr/bin` path.  So to run Java 9 without removing Java 8 or creating an Ubuntu package, I can simply add Java 9 executable to the start of the system path so it is picked up first.
  
  To make the manual adding of Java to the path more robust, I use the environment vairable `JAVA_HOME` and set that to the location pointed to by the `current` symbolic link.  If I want to try a new version of Java I can simply change the symbolic link.
  
  Add the environment variable to your shell resource configuration, eg `~/.bashrc` or `~/.zshrc` as follows
  
```bash
### Java9 - from https://jdk9.java.net/download/
export JAVA_HOME=/home/jr0cket/apps/openjdk/current
export PATH=$JAVA_HOME/bin:$PATH
```  

  Now when ever I open a new command line terminal I can run Java 9 as the default Java.  I could also use `source ~/.bashrc` or `source ~/.zshrc` command to update the path in the current command line terminal. 
  
#### Testing Java 9

  To test I have successfulling installed Java 9 I run the following commands:
  
    java -version
    javac -version

  To test the speed performance of Java 9 over Java 8 I used Light Table, a modern and easy to use development environment for Clojure.  For my performance test I opened a small project in Light Table and opened its main Clojure file.  I then started an Instarepl in Light Table for the current file.  
  
  Using Java 8 the Instarepl took 17 seconds to start up.  Using Java 9 the Instarepl took 14 seconds to start up.

> The time taken for the REPL to start included checking for dependencies each time I ran it.  In each test the dependencies were all ready present so time difference is not due to downloading libraries.  There are many more tests I could run, but the biggest difference for me is in REPL startup time.

  So in this basic test there is a visible improvement in REPL startup time with Java 9.  I hope that this startup time can be further reduced as Java 9 develops and the componentisation of Java via Project Jigsaw helps make Java smaller and quicker to start.

Thank you.
[@jr0cket](https://twitter.com/jr0cket)








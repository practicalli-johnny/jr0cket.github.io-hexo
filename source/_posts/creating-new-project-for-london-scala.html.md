title: Creating a new project for the London Scala coding dojo
date: 2011-01-25 00:13:00
categories: dev-tools
tags: 
- git
- scala
---

{% img img-thumbnail http://upload.wikimedia.org/wikipedia/en/8/85/Scala_logo.png %}

On the third Thursday of the month the London Scala user group runs a Scala coding dojo at Thoughtworks office.  The event has a great atmosphere and is a really fun and friendly place to learn and practice the Scala programming language (and some TDD / BDD).

For the Scala coding dojo I use the Simple Build Tool (SBT) to create a new scala project as well as run the building and testing of that project during the dojo.

<!-- more -->

The coding dojo usually uses a kata problem from the [coding kata catalogue](http://codingdojo.org/cgi-bin/wiki.pl?KataCatalogue).

The longer term aim is to work with other coding dojo groups in London and write bots for a game engine that is being developed by the python dojo.

# Create a Git repository on assembla.com

Go to the [LSug Assembla.com website](https://www.assembla.com/spaces/lsug-dojo) and create a new Git repository: `Admin tab > Tools > Repositories > Source/Git`.

A new Git repository is created with a default name (lsug-dojo.x.git).  You cant change the name but you can give the repository a label to make it easier to locate when browsing Assembla.com.

# Clone the repository 

In order to use the repository, you take a copy of the complete repository using a git client (an IDE or git on the command line)

    git clone [repository private address]

> Note that you need to upload a public key generated on you computer to Assembla.com before you can clone a repository using its private address.  Using the private address of the git repository allows you to push changes back to the repository on Assembla.com.

# Create an SBT project

To create the sbt project, change directory to the root of the git repository you have just cloned.  This directory should be empty save for a `.gitignore` file.

Run the command `sbt project-name` and you will be prompted with questions on how to create the project

``` sbt project-name 
Project does not exist, create new project? (y/N/s) y
Name: LSug Dojo - FizzBuzz  
Organization: LSug
Version [1.0]: 
Scala version [2.7.7]: 2.8.1
sbt version [0.7.4]: 
```

The answers above will create a new Scala project using Scala 2.8.1.  A standard project structure is created

    lib  project  src  target

# Create a readme file

In the top level of the project (same folder you issued the command line) create a `README.md` file and enter a basic overview of the project.

# Add suitable git ignore settings

Edit the `.gitignore` file and add the following lines

# Add testing framework </span>

Originally we used a test driven development framework such as JUnit.  Now we prefer a Behavior Driven Development approach and therefore use ScalaTest, although we may switch over to Specs to compare the differences.

Either way, the test framework dependency needs to be added to the SBT project, so the framework library files will be downloaded and managed by SBT.

Once the project has been created, create a new text file (and folder structure if necessary) called `project-name/project/build/dependencies.scala`.

Here is a sample `dependencies.scala` file that adds dependencies on ScalaTest and Scala check

``` dependencies.scala 
import sbt._

class ProjectName(info: ProjectInfo) extends DefaultProject(info) {
    val scalatest = "org.scalatest" % "scalatest" % "1.2"</span>
    val scalacheck = "org.scala-tools.testing" % "scalacheck_2.8.1" % "1.8"</span>
}
```

# Ask SBT to update the project dependencies

SBT does not automatically download the dependencies for you, it waits until you are ready.  When you have run `sbt` in the project folder and have the sbt command prompt, run the `update` command to load in the dependency changes and download the appropriate library files. 

# Commit / Push changes back to Assembla.com repository<

Commit all the local changes and supply a suitable change message

    git commit -m "Initial SBT project setup and readme.txt"

Push the committed local changes back to the git repository on Assembla.com

    git push origin master

# Project setup at the Coding Dojo

When setting up the coding dojo laptop, go to the top level directory of the project and run the `sbt` command.  This will put you into the sbt shell, where you can then compile your code and run tests.

# Running the tests continuously

Run the `~tests` command to automatically run all tests when file changes are detected.  Every time a save is made to your code and test files, all the tests will automatically run. 

If using git on the command line, open a terminal for git commits during the coding dojo.  Commits should be done when the pilot's 10 minutes is complete.  Commits can also be done during those 10 minutes at the pilots discretion.

# Create a project in IntelliJ

Create a new Scala project with existing sources.  IntelliJ is only used for writing the code and tests as in our previous experiences IntelliJ is too slow to compile the code.  Using SBT to continually compile and run tests always ran faster.

Thank you.
[@jr0cket](https://twitter.com/jr0cket)

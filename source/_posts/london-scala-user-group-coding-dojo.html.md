title: London Scala user group - coding dojo
date: 2010-12-20 11:42:00
categories: events
tags: 
- scala
---
{% img img-thumbnail http://www.scala-lang.org/sites/default/files/newsflash_logo.png %} 

A coding dojo is a form of deliberate practice where you are concerned with improving your software development approach and language skills.  The aim of the Scala coding dojo is to learn how to think in terms of the Scala language and functional programming constructs.  The reward from a Scala coding dojo is in that you feel more capable with the language and you learn a little (or a lot) more each time.

<!-- more -->

Focusing on the delivery of a solution detracts from the learning experience, so the aim of a dojo is to practice over and over again, building confidence and experience.  A preoccupation with finding the best solution often leads to long discussions where no practice is taking place.

Although creating fully working software projects is not a goal of the dojo events, regular attendance at the coding dojo should increase the number of members who are able to work on Scala projects productively.

# The approach

A single computer is used throughout the dojo, connected to a projector so everyone in the room can see what is going on.  This computer has the Scala coding dojo environment installed (currently IntelliJ IDEA, Scala 2.8, ScalaTest, SBT).

People take it in turns to pair program on the computer, pairing for 10 minutes at a time.  Using 10 minute cycles helps to keep everyone involved in the dojo and prevents one person or pair from going off on too much of a tangent.  Using a 10 minute cycle also helps to focus on writing the next step and not getting too ambitious and getting themselves into too much difficulty.

The pair is strongly encouraged to discuss out loud their approach to help keep the audience engaged and it also helps the pair focus on what they want to achieve next.

The Scala coding dojo uses a test driven development (TDD) approach, writing a test to codify a single piece of behavior in a "test" and then writing code to make that behavior work.  No code should be written without writing a test.  This test first approach is very valuable in the dojo as it allows the current pair working on the solution to explain to the audience there thoughts on the next step to solving the problem.

## Managing code projects 

The coding dojo project is managed in a [public Git repository on Assembla.com](http://www.assembla.com/code/lsug-dojo/git/nodes?rev=master) so that the code is easily shared and modified by anyone.&nbsp; Using the [wiki from Assembla.com](http://www.assembla.com/wiki/show/lsug-dojo/) the LSug members have contributed lots of information about the development environments and the problems we have tackled.

# Recommendations

Relatively simple problems often work best, especially when you are starting out with the dojo and it is common to start with some of the [coding Kata](http://scala.jr0cket.co.uk/practicing/coding-kata) problems you can find on the Internet.  Kata problems are a good measure of how focused you are during the coding dojo, as when  you get into a good rhythm then as a group you should be able to complete a kata problem in one dojo.

Establishing a productive environment for writing and running tests and code, makes the dojo a lot more effective.  Regularly running tests over the 10 minutes of a dojo session gives the pair at the computer lots of feedback and helps them keep on track.  The tests should therefore run very quickly and be easy to run, preferably tests run automatically when any changes are saved and the results shown within in a few seconds.  For the Scala coding dojo we use Simple Build Tool (SBT) to create a project and inside that project run the ~tests command to continually check for tests to run.  

Balancing the skills of those pairing together is very important with anyone who is new to Scala or a coding dojo placed with someone who has more experience.  This balanced pairing is very effective for the individuals learning and for keeping the dojo progressing at a good enough pace to keep the audience engaged.

Gaining consensus and deciding on a particular approach to the set problem is a very useful activity when starting a new problem.  As people are learning they often have different and conflicting approaches to addressing the set problem.  It is therefore more effective to get everyone in the same direction by selecting a high level approach to solving the problem.  For the Scala dojo this includes deciding on several aspects of functional programming and design and which approach we would like to try for a particular dojo session.

# Sponsorship
The London Scala user group coding dojo is sponsored by [Thoughtworks](http://www.thoughtworks.com/) UK, who kindly provide the venue and refreshments.  _Update: the event is now sponsored by YouDevise_ - **2nd update: the event is now sponsored by Tim Group (formerly YouDevise)**

Thank you.
[@jr0cket](https://twitter.com/jr0cket)

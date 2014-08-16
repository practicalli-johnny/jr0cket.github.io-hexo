title: Agile overview - Extreme Programming
date: 2012-04-16 13:24:00
categories: agile
tags: 
- agile
---

{% img img-thumbnail http://1.bp.blogspot.com/-qneIw3F_ftM/T4vb6mCVcII/AAAAAAAAHaA/1EQiEvxTotQ/s1600/Fear_and_Loathing_in_Las_Vegas.jpg %} 

> "If a thing like this is worth doing at all, it's worth doing right" - Hunter S. Thompson, [Fear and Loathing in Las Vegas](http://www.imdb.com/title/tt0120669/).

This is my simplified way of describing the approach of extreme programming.  Everything that is valuable is done all the time, because it is valuable.  So as creating a test has value for the design of your classes you should do it for all of your code.

<!-- more -->
# Overview

Extreme programming is a set of common sense practices that when used together can give you a better chance of having a software team that is can do what you want, tell you how much it would cost, deliver quality code with a robust set of tests, allow you change what you want when you want or change your mind at any time.

{% img img-topic http://4.bp.blogspot.com/-akzobs3MO88/T4vaoqDR8bI/AAAAAAAAHZs/IXS-eJNgNFE/s1600/extreme-programming-practices-RonJeffries.jpg %}

In this article I'll cover some of the more interesting and contentious aspects of extreme programming.

# Unit testing

Its easy to add the JUnit (xunit, nunit) library to your project and start wringing code that tests your code.  Its easy to reach a whole test suite that will give you 90% code coverage, as measured by [Clover](http://www.atlassian.com/software/clover/).  However, that is not where the value of unit testing really lies.

If you believe tests are important, then why not do them before you write the code.  In fact why not create the tests to help test your assumptions of the story you are about to write.  If you cant understand how to test out your story before you write the code that implements it, do you really understand that story enough?

You get the most out of unit testing when it is used as a design tool, helping the developer model the behaviour of the system before committing it to code that will end up in production.  Using unit testing as a design first tool helps you keep your code simple and elegant and far more maintainable.

As a consequence, you get an automated set of tests for your code.  These automated tests will help manage regressions should you need to refactor, although if you have designed your code well then changing your code should be relatively straight forward and guide developers from introducing bugs.

Writing good unit tests comes down to understanding the behaviour of the software you have been asked to develop.  A great way to validate this understanding is to talk to someone else about it.

# Pair programming

Its unfortunate that many developers do not want to pair or that managers see this as a waste of resource.  Pairing (it can be more than two people) is an invaluable way to create code (and tests, documentation, design, etc) as you always have someone there to check your assumptions with.  Its very easy to get lost in the creative design of your software and loose the bigger picture, especially when you are in the coding zone.  Having someone with you to support and question what you are doing produces far greater understand, better designs and more elegant code.

Pairing is also a great way to build collaboration in a team as well as share knowledge and experience throughout the project.  With all these benefits you would be crazy not to encourage this practice.

**[Atlassian Bitbucket - spooning video](https://bitbucket.org/spooning/)**

# Collective code ownership

When everyone owns the code and everyone is responsible for the quality of that code then you get better code.  Collective responsibility encourages the team to share design ideas, share understanding of the project, share their own experience and help each other learn more about the overall project.

Its great to see that so many developers are getting back to the code review, using tools like Crucible which make it very easy to review in a more social way.  When commits are linked to stories or bug fixes then it enables the team to quickly check just the code that has changes, making reviews more productive.

With the advent of dvcs and social code sharing, developers have become more comfortably sharing there code and learning from each other.  With easy branching (forking) it becomes trivial to experimentation with someone elses code and pull requests make it so much easier to share code changes, especially for distributed teams.

# On site customer

Some companies actually go out of their way to only work with a customer if they are on site as it makes such an impact on the risk and success probability of a project. 

Developers need a clear understanding of the work to be delivered and the priority in which the customer values it.  These aspects are in a constant flow of change, in the same way that the customers business is constantly changing (as there customers are also going through changes).

[Seibert Media](http://www.seibert-media.net/) are such a company using this and many other agile techniques to help them deliver with confidence and have highly satisfied customers.  They have had such a great success with on-site customers that they include this as a requirement for any project they engage with.

# User stories

User stories are the agile way to define requirements for a project.  Instead of large unweildy documents, the agile approach is to use story cards of a fixed size that purposely limit the amount of detail.

So user stories are the requirements broken down into small pieces of functionality, so they can be more easily understood by the whole team.  As the project functionality is broken down, conversations about the specific details and priority of things happen.

User stories are a place holder for all the conversations that you want to have around that piece of functionality.

# Creating different Persona 

Teams often add context to user stories by also defining personas.  Personas are a caricature of a user role, that helps the whole team thing about what that person would do in a particular situation.

A persona is give a memorable name (Alan the Accountant, Suzi the secretary, etc) and a general description of them is made.

A persona, first introduced by [Alan Cooper](http://www.cooper.com/), defines an archetypical user of a system, an example of the kind of person who would interact with it.  The idea is that if you want to design effective software, then it needs to be designed for a specific person.

# Acceptance tests

How do you know when you are done? 

Acceptance tests are a natural language way to define the behaviour of the software to be developed.  As with Unit Tests these should be written before the code and are often done using tools like fitness or cucumber.  These "tests" are linked to and run on top of your code so its easy to see progress in a meaningful way for both customers and developers.

Acceptance tests are also a great way to get feedback and enhance understanding between the development team and customer - _you dont have to wait for the demo to update customers_.

# Small releases

The smaller your releases the sooner you get feedback from the actual users of the system.

> The plan never survives the war - "Stormin" Norman Schwarzkopf

Is it not always the case that no sooner has a project been delivered that the users want lots of new changes?  Instead of expending a massive effort to guard against this, why not embrace this challenge and just release your project in small pieces as often as possible to the users.  You will get all the feedback you need and will be in a better position to deliver a desirable solution that meets the actual needs of those user.

Iterations should be inclusive of project delivery and real customer usage.

{% img img-code http://2.bp.blogspot.com/-ZankjAEvCco/T4vapUz6nRI/AAAAAAAAHZ0/6YVVO1XNDxs/s1600/extreme-programming-project.gif %}

# Story estimation
Estimation is very decisive in general, so it merits its own article: [Estimates are not promises](http://blog.jr0cket.co.uk/2010/08/my-favourite-estimation-technique.html)

# In Summary

There is much more to extreme programming so I hope this has set the scene for why I believe these techniques are invaluable to software development.  Extreme programming practices are used in part or in full by the all the successful agile teams I have met.

# References 

* [Extreme programming: a gentle introduction](http://www.extremeprogramming.org/)
* [Ron Jeffries: XProgramming.com](http://xprogramming.com/)
* [Wikipedia: extreme programming](http://en.wikipedia.org/wiki/Extreme_programming)
* [Junit.org - unit testing framework for Java](http://www.junit.org/)

Thank you.
[@jr0cket](https://twitter.com/jr0cket)

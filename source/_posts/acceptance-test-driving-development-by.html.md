title: Acceptance-test driven development - John Smart
date: 2010-02-14 15:30:00
categories: agile
tags: 
- bdd
---

{% img img-thumbnail http://skillsmatter.com/custom/geeks/john-smart.jpg %} 

A summary of the Acceptance-test driven development talk presented by [John Smart, principal consultant at Wakaleo Consulting](http://skillsmatter.com/expert-profile/agile-testing/john-smart) - held at [Skills Matter](http://skillsmatter.com/) by the [Agile Testing user group](http://www.meetup.com/agiletesting/) on 11th February 2010.

Acceptance testing is a a key agile practice, especially in practices such as behaviour driven development (BDD) and test driven development (TDD). 
<!-- more -->
The main benefit of acceptance tests in agile are not the tests themselves, but the ease in which they allow people to communicate.  The language of the tests is expressed in the business language (industry domain) usually in a simple to understand structured natural language (often with spreadsheet style tables for typical and edge case data examples).

As the tests are expressed in a business language, they can easily come from the business (customer / product owner).  As the language used to write the tests should be universally understood in the team, it is easier for the whole team to work collaboratively on them.

Using the Given-Then-When structure of BDD, the acceptance tests are also in the perspective of the user.  The tests focus on what the system does and not how the sysem does it (as was mentioned previously at the last agile testing talk by Gojko - this helps keep a seperation between the acceptance tests and the details of the code written).

# Acceptance tests are executable!

EasyB, Fitnesse, JBehave and Cucumber are examples of  tools that allow you to execute acceptance tests very easily.

Being able to run the acceptance tests at the drop of a hat is a very powerful way to determine when a feature has been implemented in code.  The tests can generate (html) reports as well as being integrated with continuous integration systems eg. Hudson CI and web testing tools such as Selenium.  All these tools can be integrated as one build process, so when code is checked in or acceptance tests added, every aspect of that change is managed.

# How far do you go?

Acceptance tests are very inefficient to debug your code, as are testers and coders.  Finding bugs is wasteful, preventing bugs is much more effective.

When writing acceptance tests think in terms of a story, a happy path of how the system would be used.  Then elaborate your tests as you become more in tune with the users of the system (users also include other systems)

By writing acceptance tests in terms of what the system should do, avoids those tests becoming a lag by having to refactor your acceptance tests for code changes.

Please [review the slides and the video](http://skillsmatter.com/podcast/agile-testing/john-smart-acceptance-test-driven-development) from the event for examples of using EasyB and how easy it is to use the BDD style language of Given-Then-When for writing your acceptance tests.  Also, visit the [Agile Testing user group](http://www.meetup.com/agiletesting/) and get involved in the agile testing community.

I would encourage to you to visit the [Skills Matter website](http://skillsmatter.com/) for lots of upcoming talks on agile testing, BDD and many more excellent topics.  I am attending [a BDD workshop on the 26th February by the formidable Liz Keogh](http://skillsmatter.com/course/agile-testing/bdd-immersion-workshop-behaviour-driven-development-for-developers), I recommend looking this course up if you are interested in learning BDD effectively.

Thank you.
[@jr0cket](https://twitter.com/jr0cket)

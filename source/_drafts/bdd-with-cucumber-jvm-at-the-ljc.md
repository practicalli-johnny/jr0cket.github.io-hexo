title: "bdd with cucumber jvm at the ljc"
date: 2015-08-11 18:35:20
categories: events
tags:
- bdd
---

Created in 2008 by Dan North and Aslak Hellsok

You should spend some time understanding BDD before just downloading Cucumber and writing test

Balancing the problem domain with the solution domain - Erick Evans, DDD

Its very hard to get into a particular domain as a developer

Frank Knight - known knows... quote stolen by Donald Rumsfeld.

What do we do about the unknow unknowns ?  We get to know these eventually once we deliver the software to the users

By discovering a question, you can turn an unknown unknown into a known unknown, giving you an opportunity to reduce the risk of that unknown.

What do BDD'ers do

- conversations
- concrete examples
- automated tests - that are a specification written (just) before we write the code


the idea of pidgin language was used to help shape the language of cucumber - pidgen french is the very simple language the french created to talk to the natives in their coloneys.

Given is where you set up a context
when - and event
then - the expected outcome

In cucumber you would set up the context, maybe by clearing the database and adding just the specific data needed.

Business people and product owners are now discovering Cucumer as a great way to effectively communicate with developers.  Having a simple, clear, structured language that trys to minimise ambiguity, usually translated to a more desired product in the end with fewer issues.

# Who writes features & scenarios

Edward Demming went over to Japan after the 2nd world war to find a smarter way to build up their manufacturing industry

Lets make toast the American style - you burn, I'll scrape - Edward Demming

This statement is about defects and waste.  If you dont get something write the first time, then you have to fix once you have created it.  This becomes very expensive.



# Research
- ports and adapters - a pattern to separate business logic from UI by defining a clear and minimal public api - rather than making everything public.


title: "NorDevCon - Exploration of Symbiotic Design Practice"
date: 2016-02-25 10:04:38
categories: 
tags: 
---

Agile has set a great grounding in software development however most of the discussions are around "hey, I'm doing agile" without discussing specific practices.  Some agile development teams are only addressing a part of the problem with agile.

XP defined a range of tools and practices to make the development team more effective.  Scrum focused on making the company work more effectively.  Business people are experts on the business and development teams are the experts on building systems, so if there is a healthy and valuable working relationship then the company is more effective at delivering the right systems at the right time.

However, there is still a schism between developers and business (even if that's the same person)

Developers can feel pressured to give short estimates, however developers often are over optimistic or too focused on pleasing the business in the short term.  However then the business is not well served when what is delivered is over run or of lower quality because it has been rushed.

> The Law of Leaky Abstractions - Joel Spolsky

Agile told us there could be this abstraction layer between business and features, however there are more to software development than features and schedule.  Above a certain level, all we see is work (stories, tasks, features)

The software has dependencies and changes impact the quality.  Its easy to start writing technical debt and quickly degrade the sustainability of the software.


> Theory: Broken windows - as soon as you see a broken window in a city then looting becomes more rife.  If you fix any breakages straight away, looting and breaking windows is less likely.  The same thing applies to code, if you start in a position where you write clean code, others are less likely to diverge from that and everyone writes clean code (no one wants to be different)

Unruly have a visual developer skill matrix so people know who to reach out for in terms of experience and expertise.  It would also be great to see a continually updating view of the quality of the software codebase(s)


Surfacing knowledge

Retrospectives on the health of the business
- give people grades on the quality of the software overtime, they can see the impact on the decisions that they make.

Different ways of communicating technical debt to the organisation


# Estimation game
Estimate a series of features and order them in the linear way you are going to develop them, taking care of any dependencies.  As you process each feature, all the other features are adjusted by a random element, either up or down.

Additions
- if the points get above a certain level, management hire more developers and you add another 10 points to the cards
- adding more cards
- re-planning the order of the cards
- adding a developer not using clean code, so a refactor factor is added
- technical debt factor - incrementally increasing the adjustment factor exponentially
- not including tests - once you reach a certain level of complexity, the adjustment factor is doublled
- factoring in a re-write

# Feature teams

Most agile teams have gravitated to a feature based organisation where people are exposed to a range of components in the system.

One concern with feature teams is that they may not care as much about a particular set of components.

> Conley's law - the structure of a large enough system models the structure of the organisation that created it.

> Dunbar's number - the maximum number of people you can interact with and still remember their names... (TODO: add to Devangelist)

# In Summary

Code is like biology in that it keeps growing and growing and growing.  The code becomes intractable and its like 

Thank you.
[@jr0cket](https://twitter.com/jr0cket)

title: Why tools are important
date: 2010-12-14 15:48:00
categories: dev-tools
tags: 
---

{% img img-thumbnail http://4.bp.blogspot.com/-FdwbEsaReXo/T4g-OiS_IbI/AAAAAAAAHOU/UvAHsOzrTtw/s1600/tools-huge-swiss-army-knife.jpg %}

Software development tools such as [JIRA](http://www.atlassian.com/software/jira/), [Netbeans](http://netbeans.org/), Eclipse, Git, Maven etc. are what most people consider when mentioning tools.  In the context of this article I consider tools in the wider scope, a tool can be a process or a particular practice (TDD, pair programming) or a persons creative thinking, these are all tools that we use to help us achieve some goal.

<!-- more -->

Introducing tools can be a great way to break the status quo and get people talking about the concepts around the tool, giving people a trigger to start thinking more specifically about what they are trying to achieve.

Just relying on a tool can lead to its own problems though.  If those using the tool dont have a clear goal in mind or understand what value they can get from a tool, then its use will either decline, be circumvented altogether or simply abused. 

The software development team will often lead the way by introducing tools but the operations teams concerns also need to be addressed so that the tool can be come established and the most benefit gained.

# Example: Introducing distributed version control (eg. Git)

DVCS are great productivity tool for a development team and can be used to great effect  to allow the developers freedom to explore challenging aspects of a code solution (spikes) whilst not polluting the code base or having to deal with difficult merges.

Introducing dvcs needs to support the release process though and not descend into anarchy.  By involving the operations and release management roles, a DVCS tool can be more effectively embarrassed by the whole team, addressing a wide range of concerns

In the example of the Linux kernel, there is one central master repository which is used for release, but no direct commits are done to that repository.  Instead, decentralised repositories are used to commit code by a wide range of distributed developers.  Then a release manager role is used to merge (pull) useful code from the decentralised repository into the central master, from which coordinated releases take place.

Thank you.
[@jr0cket](https://twitter.com/jr0cket)

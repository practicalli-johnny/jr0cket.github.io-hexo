title: 7 continuous integration ideas from CITCon
date: 2011-11-14 09:49:00
categories: events
tags: 
- ci
---

{% img img-thumbnail http://3.bp.blogspot.com/-o7Pc-gAcjRA/Tsfch5XZo4I/AAAAAAAABIE/2W2eCc58fi4/s1600/citcon-schedule.png %}

CITCon is the most intense event I know on the subject continuous integration, continuous deployment / delivery and [DevOps](http://en.wikipedia.org/wiki/DevOps).  Discussion raged on throughout the day although we manage to keep it to minor scuffles when talking about feature branching... 

With so many ideas to process after the event, here are _my top 7_ to start with.

<!-- more -->

{% blockquote @PaulJulius %}
Any practice that disallows refactoring is bad. So if you can't feature branch and refactor, then don't do it." [#citcon](https://twitter.com/citcon)
{% endblockquote %}

# 1 - Understand the implications of DevOps

{% img img-topic http://4.bp.blogspot.com/-FGBBSNoCUjc/TsFIdoAEgXI/AAAAAAAABH0/rwLXVfbSKHw/s1600/citcon-patrick-debois-discussing.png %}

[Patrick Debois](http://www.jedi.be/) first coined the term [DevOps](http://en.wikipedia.org/wiki/DevOps) and it was great to have his insight at the conference.&nbsp; There is still a gulf between developers, testers and server teams resulting in most software being very hard to deploy.&nbsp; There is a broken feedback loop in many companies and even doing something as simple as talking to the server team about deployment can start you on the road to great improvements.

Patrick is currently working with [Atlassian](http://www.atlassian.com/) to help with their [OnDemand](http://www.atlassian.com/software/ondemand/overview) SaaS offering, helping improve the deployment process by understanding how well we monitor and report on our systems.

# 2 - CI is more than just running Jenkins

{% img img-topic http://3.bp.blogspot.com/-IJLF9DdXXns/Tsfj-fAS3EI/AAAAAAAABIM/-8RB5BZVNTs/s1600/spring-project-stats.png %}

Getting continuous integration working well for your company is still a challenge for most.&nbsp; Whilst its pretty simple just to plug your builds into the CI server and get it to run your tests, that raises more challenges in itself:

*   How often should we run our builds?
*   What actions should be in our builds?
*   What information should our builds tell us?
*   What do the results mean?
*   How can we improve the way we do things?An important step is to work out what you want to get from CI, with in the context of your software development efforts and the wider business goals.

# 3 - If its painful, do it more often - if its fun, do it more often

{% img img-topic http://3.bp.blogspot.com/-zr6AbVn-gKQ/TsfoJrtZ-RI/AAAAAAAABIU/eje5EYG1lJo/s1600/feedback.png %}

Deployment is often a painful experience for teams and by delaying deployment and not doing deployment dry runs a vicious cycle forms.&nbsp; As its painful, teams shy away from deployment - so when the time finaly comes there is much more to deploy and more opportunity for things to go wrong.

If its painful, do it more often so you learn how to manage and reduce the pain.&nbsp; As with code tests, the more often you run them the more feedback you get and the quicker you can resolve issues.

Carrying out dry runs of the deployment in different environments is invaluable and less risky that production.  Dry runs can be wiped and carried out again and again helping to ensure a smooth deployment and gather feedback to make the process more effective.

{% blockquote @jr0cket %}
A nice addition to "if its painful, ..." & "if its valuable, ..." RT [@patrickdebois](https://twitter.com/patrickdebois): #[citcon](https://twitter.com/citcon) : if it's fun, do it more often.
{% endblockquote %}

# 4 - Understand what is important

{% img img-topic http://4.bp.blogspot.com/-1DzeOK7WsHc/Tsfpyud-agI/AAAAAAAABIc/67IHMxG-mao/s1600/Tesco_value_droid.jpg %}

Developers that understand the needs of the company they work for and the concequences of their actions are the ones that truely become invaluable and help a company be successful in a sustainable way.&nbsp; Whilst some companies can survive [Mortgage Driven Development](http://skillsmatter.com/podcast/agile-testing/refuctoring-your-cukes) for a little while, most will suffer badly.

When going beyond the basics of CI and moving to a continuous deployment / delivery approach, a solid understanding of the business is vital if you want to improve in a positive direction.

{% blockquote @jr0cket %}
Great session with @[benjaminm](https://twitter.com/#%21/benjaminm) on what we can learn from CI @[citcon](https://twitter.com/#%21/citcon "citcon") [ow.ly/7rqM2](http://t.co/fFUFWmxr)
{% endblockquote %}

## 5 - Visualise everything

{% img img-topic http://1.bp.blogspot.com/-OsygFpW182k/TsfurrewS9I/AAAAAAAABIk/LB7q7ApPMho/s1600/web-traffic-monitoring-with-Woopra-live-full-interface-450.gif %}

Understanding you system requires a good amount of monitoring and reporting on events.&nbsp; There are a wide range of tools, such as [Nagios](http://www.nagios.org/) that will produce detailed reports and real time warnings of issues.

Some issues can only be seen historically, so as you build up monitoring information you can identify patterns of behaviour and discover ways to avoid issues and improve the way the system works.

Also visualise the way you work and the way teams work together using techniques like wallboards &amp; kanban boards.

# 6 - Keep learning

I think the following tweets show the diversity of subjects covered @CITCon and the sheer enjoyment that can be had in the software development world.

{% blockquote @andrew %}
Organisational anthropology is a mechanism to incite or suppress insurgency. Didn't expect that at conversation at [#citcon](http://hootsuite.com/dashboard# "citcon") 
{% endblockquote %}

{% blockquote @jr0cket %}
Great fun talking about BDD, Cloujre, CI Server build jobs, visualisation, wallboards and double loop learning @[citcon](http://hootsuite.com/dashboard# "citcon")
{% endblockquote %}


## 7 - Robot testing is cool

{% img img-topic http://farm7.staticflickr.com/6227/6338844678_1a52146878_b.jpg %}

Playing with robots is cool, watching robots automatically run tests on an Andriod phone playing Angry Birds was amazing.


# Thank you to...

Thanks to [@PaulJulius](https://twitter.com/#%21/PaulJulius "PaulJulius") and @[@jtf](https://twitter.com/#%21/Jtf "jtf") for organising [@citcon](https://twitter.com/#%21/citcon "citcon"), Squirel and TIMGroup for sponsoring such a successful event.  Wendy and the rest of the [SkillsMatter](http://skillsmatter.com) crew for hosting and [filming the event](http://skillsmatter.com/event/agile-scrum/citcon).


## Some final tweets for thought

{% blockquote @benjaminm %}
Using Chuck Norris to discuss negative behaviour
{% endblockquote %}

{% blockquote @jtf %}
Legacy code is only a problem for successful products
{% endblockquote %}

{% blockquote @PaulJulius %}
Are your [agile] stories boring you? Then write more interesting stories. Improve the language. Adjectives, adverbs... 
{% endblockquote %}

{% blockquote @PaulJulius %}
Notion: both feature branches and feature toggles should be short lived and aggressively tested.
{% endblockquote %}

{% blockquote @illicitonion %}
Cucumber is an assumed starting point at [#citcon](https://twitter.com/#%21/citcon "citcon"), interesting
{% endblockquote %}

{% blockquote @PaulJulius %}
In Feature Branching discussion. Reminds me of the [blog I wrote a while back](http://t.co/A0TqduxD)
{% endblockquote %}

{% blockquote @Steve_Boone %}
CD is about delivering confidence
{% endblockquote %}

Thank you.
[jr0cket](https://twitter.com/jr0cket)

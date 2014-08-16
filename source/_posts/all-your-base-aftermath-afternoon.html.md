title: All your base aftermath - the afternoon
date: 2012-11-23 16:37:00
categories: events
tags: 
---

{% img img-thumbnail http://3.bp.blogspot.com/-mf5oQ5REbLA/UK_KqBKfA9I/AAAAAAAAIlg/NkVH_v20CLM/s1600/all_your_base_conf_2012.png %} 

The second half of All your base was just as great as the first, although there was so many interesting ideas and new shiny things to try I will be busy through the holidays trying to process it all.

The talks this in the afternoon treated us to a feast of: Git as a NoSQL db, Redis, MySQL at Twitter, LawnChair mobile web persistence, Postgres Demystified and Apache Cassandra.  What follows is just some of that data goodness...

<!-- more -->

# Postgres Demystified by Craig Kerstiens, Heroku

[slides](https://speakerdeck.com/craigkerstiens/postgres-demystified))

[Postgres](http://www.postgresql.org/) is a really powerful database yet still feels pretty lightweight to use and a world away from the heavy-duty admin required for other "enterprise" db's.

Postgres is also one of the most innovative relational datbases out there, long having an object-relational model and [Multiversion Concurrency Control](http://en.wikipedia.org/wiki/Multiversion_concurrency_control) (MVCC) to keep data really safe.  Support was recently added for storing data in the [json](http://json.org/) format and you can even hook Postgrest up directly to [Redis](http://redis.io/).

With so many features it often referred to as the **emacs of databases**, in that it can really do so much more than most databases.

So its no surprise then that the popularity of Postgres has grown over the last few years and that companies such as Atlassian and Heroku run their businesses on it.

{% img img-topic http://3.bp.blogspot.com/-Nsye5ICWkTY/ULzEtFbtc2I/AAAAAAAAInk/Pv7TAovtJd0/s1600/mac-boo-pro-sideon-lid-closing.jpg %} 

One bug-bear for developers was trying to get postgres installed on a Mac, it was far too painful.  So the team at Heroku created an app for that at [http://postgresapp.com/](http://postgresapp.com/).  Now its just a matter of a download and dragging the .app to your applications folder.

Otherwise, PSQL is a really easy to use terminal client for Postgres. PSQL enabling you to execute queries interactively and see the query results instantly.  PSQL also supports tab completes and `\e` allows you to edit the commands directly in what ever is your default shell editor (emacs, vim, etc).  PSQL also provides meta-commands and various shell-like features to facilitate writing scripts and automating a wide variety of tasks, so its really flexible.

There are lots of data types supported in Postgres, including the really useful _arrays_.  As thought has been put into time based data then support for Range types and `timestamptz` is also a really so nice touch to help you prevent time conflicts.

Postgres 9.2 brings direct support for [json](http://json.org/) data type.  Coupling this with the JavaScript V8 engine that is now part of the database server you can do some very powerful things.  However, instead of just SQL injection attacks to be  wary about, it you dont manage access to your database carefully, you  could also be susceptible to json and javascript injection attacks - so use with care. 

> [@lizconlan](https://twitter.com/lizconlan) Great Postgres primer from [@craigkerstiens](http://twitter.com/craigkerstiens), totally get the emacs quote [#AYBconf](http://twitter.com/AYBconf)

# Performance tips

Using the `explain` command can help you work out inefficiencies in your database queries.  Adding explain to your queries will show you what is going to happen if that query is run and an estimate of how long postgres thinks it will take to run.

Using `explain analyze` postgres will run the query and then analyse how long the query actually took.  A good target is to aim for 10 miliseconds as a baseline.

[PgAdmin](http://www.pgadmin.org/) can also show you a graphical representation of the explain plan.

> [@craigkerstiens](https://twitter.com/craigkerstiens) your web app DB query should take 10ms at most [@AYBConf](https://twitter.com/AYBConf) [#ayb12](http://tweetchat.com/room/ayb12)

A great indexing technique is to create your indexes concurrenty, so you dont need to take you database off for a day to improve performance.

    create index concurrently _index_name_ on _table_ 

However, dont worry about indexes too much up front, wait and see how your uses work with your application and then start to optimise.

There are lots more **[reasons to use Postgres](http://www.craigkerstiens.com/2012/04/30/why-postgres/)**, as covered in a blog series by Craig.  You can also discover more detail about postgres with [Craigs online guide](http://www.postgresguide.com/).

Get a jump start by **[adding postgres to your application on Heroku](https://addons.heroku.com/heroku-postgresql)** or get **[Postgress as a service](https://postgres.heroku.com/)**.

# Git - the NoSQL database ?

We all know that Git is amazing at storing and managing source code, but how is it for data?  That was the question posed by Brandon Keepers of Github?


> [alegonbel](http://twitter.com/alegonbel) Git = the stupid content tracker [#ayb12](https://twitter.com/ayb12)

When you ask git what it is, `man git`, then it just tells you its a stupid content tracker.  That doesnt mean its a bad tracker, its just that it does not care what it is tracking, leading to the idea that Git can be used for more than code.

{% img img-topic http://2.bp.blogspot.com/-uPeHmICWqLM/UK_FbuqEBhI/AAAAAAAAIlI/R7hBrt5F4hU/s1600/git-man-stupid-content-tracker.png %}

If you look at the contents of the `.git/objects` folder for a project you can see all the files that make up the git data model.  So you can see, its not like a "traditional" data store and as its file based will have several limitations.

{% img img-code http://3.bp.blogspot.com/-A4LlPh6PMrM/UK_LcVJkdTI/AAAAAAAAIlo/Wm2PnNTMd3E/s1600/git-internals-commits.png %} 

When a file is added to git, `git add`, `git commit`, it puts that file in a blob and creates a hash of the data that is therefore unique.  If the hash is the same on two files it means that their data is exactly the same.

A tree is then created that points to that blob and any other related trees.  Finally we get back to a commit, which has a tree that is the root of the project as well as project info such as author and message.

When a new change is added to git it has to point to a point in the existing tree.  As anything existing is immutable, a new file is created as a blob with a new tree that points to.  However, that new tree can use reference a parent in the existing tree so changes are added efficiently as only the things that have changed are added to the data model.

All the great features that database systems have, git has none of those.  What git can do is:

*   Versioning - look back at previous changes really easily and create diffs of what has changed.
*   Hooks - update caches as an alternative form of indexing for searches.
*   No "big design up front" - optimize the storage based on the actual usage patterns and evolve the data structures as more discovery is made.
*   Branches - gives long lived transactions
*   Replication - a clone is a full copy of all the data and clones can be driven by hooks So Querying data is something you just have to figure out yourself.  Concurrency is a challenge as git is file system based, so when multiple people try to update then changes could be lost.  Scaling is also a really big challenge, especially when randomly updating records in git - partly this is because we are re-writing the whole tree structure to make an update.

Git also does a really bad job when it comes to handling long running projects that have grown considerable in size.  Add, status and commit commands talke longer and longer. 

So whilst its interesting to think about git as some kind of simple data store, there are a great many challenges if you want to manage big data sets within one git project. 

Brandon left us with the thought _"abuse your tools, imagine how to make them better!"_.

# Redis Steady Go

{% img img-topic http://4.bp.blogspot.com/-nDtNvipmj1g/ULACYq-_CDI/AAAAAAAAImI/8zQu6eoIM5I/s1600/redis-logo-300dpi.png %} 

> Redis is one of those great projects that when discovered by developers they really take to it.  Redis is short for _remote dictionary server_ although you can think of it as a _remote hashing server_.

Put simply it manages strings that are keys and values.  It is often referred to as a _data structure server_ since keys can contain [strings](http://redis.io/topics/data-types#strings), [hashes](http://redis.io/topics/data-types#hashes), [lists](http://redis.io/topics/data-types#lists), [sets](http://redis.io/topics/data-types#sets) and [sorted sets](http://redis.io/topics/data-types#sorted-sets). 

You can also consider redis as a Domain Specific Language (DSL) for abstract data types.  Its similar to memcache but it adds a whole lot more functionality.

There are three big uses for Redis:

*   A simple to use and work with NoSQL database
*   A messaging system, Redis comes with a publish / subscribe API
*   A web application cache (an alternative to memcache) - you can store your webpages in redis and they come out really fastSony use redis to manage the scoring from their online Playstation3 games network. Using a sorted set in Redis, millions of scores are managed for each game (as I can attest to on my poor scoring when playing StarDust).    

Pintrest also used redis as much of their content, specifically as they presented their content in terms of ranking.  All those values of all those users have to be kept somewhere.

Some important characteristics of Redis include:

*   Individual actions are atomic so data does not become corrupt
*   Single threaded
*   Event driven
*   Data can be expired
*   Replication can be done with the use of a slave and Redis is very good at live replacement.
*   Very high performance - everything is stored in memory, so its super fast.  It does have persistence though as otherwise it wouldn't be ultimately useful.
*   You can use just about any language you have ever heard of with Redis (except [Assembly](http://en.wikipedia.org/wiki/Assembly_language) &amp; [Fortran](http://en.wikipedia.org/wiki/Fortran)).
*   You can also use Redis from the Postgres databaseSo what are you waiting for, go and play with [Redis](http://redis.io/) today!  Or simply add [RedisToGo](https://addons.heroku.com/catalog/redistogo) to your application on Heroku

# In Summary

All your base was a fantastic experience and its great to see how hugely popular conferences are.  It was great to mix with people from a wider range of backgrounds that the usual developer conference.

I am looking forward to All Your Base 2013!

Thank you.
[@jr0cket](https://twitter.com/jr0cket)





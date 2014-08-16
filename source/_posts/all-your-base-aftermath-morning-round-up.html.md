title: All your base aftermath - morning round up
date: 2012-11-23 12:57:00
categories: events
tags: 
---

{% img img-thumbnails http://www.whiteoctober.co.uk/blog/wp-content/uploads/2012/10/all_your_base_conf_2012.png %}

The _All Your Base conference_ was a brilliant example of getting a  conference right.  Everything was ideal.  The venue was right next to the train station and the after party was directly opposite, so staggering for the trainback home.

The network was awesome, actually getting a hard line and even a free ethernet cable in the goody bag (because who is going to remember to bring one). 

And of course an amazing line up of speakers from cool companies including MongoDB (10gen), Heroku, Basho, MariaDB and many more.

Here is part one of my experiences at All Your Base.

<!-- more -->

# Dynamic data with MongoDB 

{% img img-thumbnails http://3.bp.blogspot.com/-URYGwZsN2CE/UK9qDsMTWdI/AAAAAAAAIj4/33Ne75f399c/s1600/mongo-db-logo.png %} 

Alvin Richards gave a great peek under the skirt of MongoDB, discussing replication, latency and how to manage data effectively in a distributed system.  Some classic authors used for the JSon examples that define the mongodb "schema".  I say schema, but MongoDB does not require an up-front schema design like a relational database.  All you need is a unique key and you can manage your data in what ever way you want using the flexible data document approach.  This allows you to have _polymorphic data_, in that you can assemble data in the way that suits your application rather than being constrained by the database product.

With all this power over the data, comes great responsibility.  It shouldn't just be a "Wild West" approach.  So good conversations are important between developers and database admins. 

> Find out more about MongoDB by [getting involved in the community](http://www.mongodb.org/display/DOCS/Community).  And try out MongoDB with your application by using the add-on available via Heroku.

# NoSQL answer to managing complex domains

{% img img-topic http://3.bp.blogspot.com/-57wTz697UCU/UK9yko6i49I/AAAAAAAAIkY/PDaHj-PYu0Y/s1600/OrientdbLogo.png %}

Graph databases are already used widely in the "friend-of-a-friend" networks like LinkedIn, although are generally new to the audience at the conference.

With a graph database you can have multiple connections between data creating a very intricate strcutre.  So whilst the graph concept is very simple, there is much to learn about using graph database well.

In a relational model, its important to focus on the design of the data relationships.  The more complexity the data relationships, the more complexity in the design of the database.  The biggest hangover from complex relational database design is the join.  If you traverse hundres of relationships then you are executing hundreds of JOINs.

The more joins you have to process the more your performance will be affected and the relational model computes that relationship every time you query the database.

> A graph database is any storage system that provides index-free adjacency - Marko RodriguezOrientDB is an open source (Apache licence) document graph nosql dbms - supports transactions, etenended,  ACID Transactions, SQL and Native Queries, Asynchronous Commands, Intents, etc.

GraphDB handels relationships as a physical Link to the record assigned when the edige is created, so traversing cost is no longer affected by db size.  Eg, traversing 30milion connections in 5 seconds 

Once you have a well connencted DB in the for of a Super Graph, you can cross records instead of query them.  All you need is some **root verticies** to start traversing.

# PouchDB because Offline data is still the reality

Voted by the WhiteOctober developers as the most interesting technology they wanted to see, Dale Harvey the creator of [PouchDB](http://pouchdb.com/) gave a great presentation using HTML5 slides (nice).  Dale currently works on Firefox OS for Mozilla and is a CouchDB contributor, so he knows what he is talking about.

Essentially, PouchDB is CouchDB for your browser.  You can use it by including the pouchdb.js script in your web code with a simple `<script>` directive.
`<script src=pouchdb.js> </script>` 

Like all flexible tools, PouchDB uses JSon as the primary data store.  This gives you a great amount of flexibility in the design and use of your data.

Under the hood, [PouchDB](http://pouchdb.com/) uses indexedDB when run in IE, firefox, chrome.  For nodejs it uses leveldb.

Why is [PouchDB](http://pouchdb.com/) here, well according to Dave - _Multi Master replication is awesome_

If you have an app and you want to work offline then this [PouchDB](http://pouchdb.com/) is a great idea.  I wish something like this was part of GoogleDocs so I could continue to edit documents when I loose connection to the Internet.  There are also many other mobile use cases where you need the data locally, not just because of limited connectivity but also for speed.

> [jr0cket](http://twitter.com/jr0cket) Offline is still a fact - people still need some data locally especially when on the move

So what's wrong with building an active sync into your app?  Well it is very challenging.  Sync'ing is very hard, especially when it comes to conflict resolution.  [PouchDB](http://pouchdb.com/) provides a very simple mechanism to handle it.  Every document is referenced by a single id, if you change the document name then is still knows its the same document.  Only when you change the id of the document does it become a different doc.  

Different changes are saved separately so it allow you to merge conflicts through the PouchDB API.

This sounds like something I'd like to include in mobile projects, so hope to get some time to play with [PouchDB](http://pouchdb.com/) over the holidays.

# Michael "Monty" Widenius - Creator of MySQL and MariaDB

{% img img-topic http://1.bp.blogspot.com/-ArH-Zpu89eU/UK9wEsiBnUI/AAAAAAAAIkQ/Sx3BeaI8KTs/s1600/mariadb-seal-flat-browntext-413x129-93172cc5c273985596a8dca78e58aa49370c4bed.png %} 

The MySQL project started from a desire to help people and do lots of travelling.  After MySQL was aquired by Sun (and before aquired by Oracle) new life was breathed into the open source project.  The original creators behind MySQL shifted to start working on [MariaDB](https://mariadb.org/), a community developed database with more features yet still compatible with MySQL.

There is no reason to use MySQL anymore, [MariaDB](https://mariadb.org/) is better in every respect.  Its completely open and all the closed source features added to MySQL has been added to MariaDB already.  It seems that Oracle has lost much of the engineering talent around MySQL and is not able to do much around the product, hence the closed source add-ons. 

> [mark_star](http://twitter.com/mark_star) "MariaDb is better than MySQL in every way" - Monty, the creator of MySQL [#betterMigrate](http://tweetchat.com/room/betterMigrate)

One goal of [MariaDB](https://mariadb.org/) is to make a bridge between Relational and NoSQL models.  Using a concept called Dynamic Columns, a proof of concept of this was done by creating a storage engine for Cassandra. 

When you want to make MySQL obsolute (which is what Monty does) then you have to provide something better to replace it.  In all respects it seems that is what the MariaDB project has achieved.  From additional in features, major performance improvements, community support and documentation then MariaDB has already become a valuable successor.

> [ciderpunx)](http://twitter.com/ciderpunx) Cool I've now got [@MariaDB](https://twitter.com/MariaDB) installed and working. All my MySQL DBs intact 

> [@montywi](http://twitter.com/montywi) Try MariaDB for yourself, it will take you less than 15 seconds to migrate, depending on how fast you type.

Break for lunch... see you soon.

Thank you.
[@jr0cket](https://twitter.com/jr0cket)

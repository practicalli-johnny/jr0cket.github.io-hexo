title: Collaborative agile practices
date: 2010-02-05 19:00:00
categories: agile
tags: 
- agile
---

For what is seen as a lightweight practice, there are a large number of techniques that help an agile team be successful.

Most people are aware of extreme programming, pairing, test driven development and more.&nbsp; Very few teams I have worked with had experience of the more creative and collaborative practices that make an agile team successful.&nbsp; Here are some examples of techniques I introduce that are often missed.

<!-- more -->

# Defining Team Values

{% img img-topic http://www.visualphotos.com/photo/1x9081555/Soccer_coach_teaching_team_values_10900009.jpg %}

Having  a set of values that the team aspires to helps bring the members closer  together and helps understanding between member of the team.

The values have to be defined by the team (usually in one or more quick  group exercises) and all team members must play a part, so they feel  they have a voice.

Getting a team to define what it values  is the first thing I do when meeting or assembling a team for the first  time.&nbsp; This is the best way I have found to get people to open up and  start working more effectively with each other.

# Product / Project values

As  with the team values, defining project values helps understand the  purpose and value of the project.&nbsp; These values help ensure people have a  shared vision for the project. These values are defined by all the  members of the team that will implement the project, usually as part of  the project of a project kick-off.  The values typically are along the  form of:

*   Create a product vision that (encapsulates the values)
*   Creates a (value type) community
*   That  (listen shares illuminates)
*   The Experience is (Inviting lively stimulating)

# Design storm

As a project team, brainstorm ideas regarding the product design using a  visual representation (eg. storyboard / conceptual model approach).  The  visual representation should keep in mind the project vision.

As the representation has been create by the team, it creates a stronger bonding and helps to ensure a shared understanding.

# Defining personas

Personas  are a way to help the team understand the needs of a range of different  users.&nbsp; A persona is a person who is created to represent a collection  of related activities.&nbsp; The persona should have a personality that  represents their values, needs and stereotypical behaviour patterns.

Personas are a great way to identify and keep in mind the the key users of the domain you are developing software for.

I use the following template to help me define a persona: 

*   Name and role - Tess the test manager&nbsp;
*   Goals - plan and track test&nbsp;
*   Motivations - detailed oriented

# Stories / Features ([MMF](http://www.netobjectives.com/glossary/7#letterm))

The  terms Stories and features are often used interchangably.&nbsp; Essentially  they are a statement of functionality defined at a common level of  detail by the team. 

Features are often defined as a deliverable piece of work that will provide value.&nbsp; This is often referred to as a [minimum marketable features (MMF)](http://www.netobjectives.com/glossary/7#letterm) and are often defined using the [INVEST](http://xp123.com/xplor/xp0308/index.shtml) principle.

In BDD, features are used to identify one or more related scenarios and are defined in the BDD language:

```
In order to _deliver some business value_
As a _stakeholder type_
I want _some specific functionality _
```

When a team is having a project kick-off, features are elaborated from the  product vision and design storm artefacts.  First identifying features  individually, converge features as a team and group those features into  sets with similar features.

# Context mapping

Draw  a context map of the feature to highlight behaviour of the user with  the system and interaction within the system at a conceptual level.  A  basic approach would be to imagine a day in the life of a user with  respect to the feature set.  [Context mapping is used in DDD for strategic design.](http://www.infoq.com/articles/ddd-contextmapping)

# Story Storm

Select a feature set and brainstorm the stories that make up that feature.

# Story examples / Storyotypes

Discuss stories and introduce the concept of [Storyotypes](http://www.springerlink.com/content/h53td341yagcc80w/) which are used to breakdown stories into manageable sizes.

# Story test

Select a story and write a acceptance test that defines a way to understand how you are going to satisfy that story.

# Class and Sequence diagrams

You  dont need to go the whole hog with UML, but defining some useful  concepts and define their relationships will help you create a high  level class diagram.&nbsp; This helps you to understand the kinds of object  that have relevance in a potential design.  You can also start to  identify context boundaries, aggregate types and have a better  understanding of the different domains in your system (see Domain Driven  Design for more on this). 

It is useful to explore the relationships between the concepts (objects) in your domain by using a sequence diagrams.&nbsp; Start with two objects and a story that they are involved with and create a high level sequence diagrams to identify the behaviour of those objects relative to our domain.&nbsp; This often gets more objects involved, creates new ones, validates others that have crop up and event give weight to removing other objects previously identified.

# Wireframes / Ux Prototypes

Often missed out by teams without creative experience in the mix, wireframes and user experience prototypes again help the team understand how users will interact with the domain and provide a weath of understanding and tests cases.

Mockups can either be sketched out on whiteboards or large sheets of drawing paper.&nbsp; Some teams prefer to use tools such as [balsamiq](http://www.balsamiq.com/) or [Pencil (firefox add-on)](http://www.evolus.vn/Pencil/).[
](http://stackoverflow.com/questions/156755/tools-for-creating-ui-prototype)

Thank you.
[@jr0cket](https://twitter.com/jr0cket)


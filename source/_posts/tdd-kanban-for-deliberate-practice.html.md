title: TDD Kanban for Deliberate Practice
date: 2011-01-08 17:39:00
categories: agile 
tags: 
- tdd
- kanban
- agile
---

{% img img-thumbnail http://picasaweb.google.com/johnstevenson1970/JR0cketJumpstart?authkey=Gv1sRgCKz2_cn7sLXg_QE#5559499396863261842 %}

To help keep you in a good flow when you are learning or practising the [TDD](http://en.wikipedia.org/wiki/Test-driven_development) test first approach, it can be useful to use a simple kanban board to manage your flow.  Here is a guide to this simple technique.

<!-- more -->

The [TDD](http://en.wikipedia.org/wiki/Test-driven_development) kanban helps you to focus on each step, helping you to stick to test-code-refactor.

The [TDD](http://en.wikipedia.org/wiki/Test-driven_development) kanban board has three lanes as follows

**Test** - you are writing a single test

**Code** - you are writing code to pass a particular test that is failing

**Refactor** - you are changing the internal workings of your code

You only have one card on your kanban board (this is your work in  progress limit), this reminds you which activity you should be working  on and should help you get into the test-code-refactor routine.

The card itself is blank and does not refer to any required behaviour or example code.

## Using the TDD Kanban board

To start, place your one and only card on the test lane of the kanban board.

Once  you have written a failing test and run your tests, move the card on  the kanban board to the code lane and write just enough code to make the  test pass.  

Once you have written enough code to make the test  pass (running all tests), move the card on the kanban board to the  refactor lane.

When you have finished your refactor work and have  run the tests, move the card back to the test lane and write another  failing test.

**Credits**

The [TDD](http://en.wikipedia.org/wiki/Test-driven_development) Kanban concept is from the [mini kanban display at Jon Jagger's cyberdojo](http://jonjagger.blogspot.com/2010/12/agile-lean-and-kanban-exchange.html) (that's my hand) at the [SkillsMatter](http://skillsmatter.com/) Lean Agile exchange 2010.

Thank you.
[@jr0cket](https://twitter.com/jr0cket)

title: devwinter 2015 aftermath
date: 2015-01-24 09:51:11
categories:
tags:
---

  A sunny and chilly Saturday morning brought the start to /dev/winter 2015 in Cambridge.  Set in the lovely study rooms of Churchill College, over 100 developers gathered to share ideas and discover new learning in a range of excellent sessions and over fish & chips and other excellent food. 

  Here are my highlights of that day.
  
#### Kill the debugger 

  This first talk by [John Cinnamond](https://twitter.com/jcinnamond) was an insightful commentary on one of the biggest pitfalls of modern development.  Its so common to program by Google or Stack Overflow, visiting them when you get stuck on a problem pretty quickly.
  
  The problem here is that 

  Of course you need Google for finding information about the technology you are using (API's, tutorials, ets) and Stack Overflow is great for examples of very specific problems.  
  
  However, to actually understand the code you are working with and all its implications, Google and Stack Overflow arent enough.  
  
>  You would be better posting your code in a public Git repository with some decent docs and asking for help.  If its code for your company, they may not want you to do that.

  Modern development has become results driven.  As developers we are given some requirements and we are expect to give something working back in return.  There is often little though as to how much the developers actually understands what they have created.

  Due to time constraints, developers often take the approach

- fill in values
- do the math
- check the result
- if its right, great, if not go back to the start 

This is refered to as [completing the square](https://wikipedia/..) 

 
If all steps are equal, then we can move the steps around 

resoning about the code is roughly equal to understanding the code

default developer approach to debugging code 
random change
run the code
check the result

then start adding print statements to see what is happening as the program runs 

<E,s> => R
Expression
State
Result

operational semantics - try and understand a program by running it and look at the state at the end.
- it doesnt tell us why it happened 

so you think, lets break down the program in to smaller steps using a debugger.... hmm 

instead, why dont we just try and understand the code 

assignment is taking us from some initial state to a new state - or joined with a new state 

denoational semantics 

obvious point: read the code so you can understand it 

how do we manage code complexity 
- hide some of the code 

or create abstractions 

a = 2 + 3
the + is an abstraction so you dont need to knw the details of the adder function 

theorems for free - philip wadler 1989
things we can get for free by looking at type signatures 

axiomatic semantics
{precondition} code {postcondition}
{k = 5} k=k+1 {k=6}

{k=6} postcondition
{k = 1

syntax and semantics of Programming languages - 

why is this useful ?  It shows correctness

Its not the proof itself its the 

it turns out that this is just like {pre}given.. {code}when.. {post}then...

so tests are not proofs, but there is enough similarity to be useful 
- tests are just for a specific context


abstractions 
- do i understand it
- can i trust it


summary
understand the code you are writing 
- pull back and take the time to understand the code 

think about how understanding works 
- we have covereds several approaches here - axiomatic, denoational, etc.

be sympathetic to understanding when coding 

dont be satisfied with the correct answer
- do I understand what I have done, will someone else understand it? 

if your code doesnt work, dont debug it... throw it a way and write again 
- we at least have to rework it until we understand the code 

panagile.com/talks/devwinter-2015 



#### Git workflow tutorial 

- governence strantegy 
- branching 
- team documenting - how does your team interact 

gitforteams.com/resources/offsite.html 
http://gitforteams.com/workshops/devwinter/


Team make up 

Roles : 
- ev's
- MVP's
- sales engineers
- managers

Responsibilities
- ev's = create / commit code / qa 
- MVP's =
- sales engineers = patches, Cloning / qa
- managers = feature requests, bugs


Rebasing rant
do you know why you are rebasing, or do you just know the command 

if you have a dispersed setup, you need a way to revise history to get multiple repo changes merged.

uses for rebase
- if you keep your feature branch together when you merge into master, it makes it easy to remove that feature from master 


#### Ditch the debugger and using logging 

cloud changes the way we must design, deliver and operate our software 

changes for cloud
- isoloate activities
- focus on Delivery
- 

Event tracing - 3 aspects 
- event type ids
- transaction tracing 
- adjusting logging levels 

event type ids
- known events 
- define events 
- unknown events 

enum 
- human readable sets, unique values, sparse, immutable 
- make the enum immutable 
- define:
--  aplicationstarted value - arbritrary large number 
-- pagegenerationstarted
-- pagegenerationcompleted



transaction tracing 
- when you move from monolithic designs to lightweight components 
- aggregate the meaning of issues across the estate of components 
- unique-ish identifiier assigned to web request 
- 

distributed systems
- remote debugging is possible but not always useful or helpful

what about appliction performance management (eg. new relic, etc)
- how much do we learn, especially as they are expensive and typically only used on production 

which log level is right ?
- debug, info, warning, error, critical, 
- log level should not be fixed at compile time
- set up event mapping configuration so different log levels are produced based on certain events 

bit.ly/TuneLoggingLevels


Event tracing 
use enumerations (or closes thing) 
technical and domain event types
distributed systems: debuggers less useful
Trace calls with 'unique enough' ...


Log aggregation 
- multiple log sources, in one place, searchable and time sequenced 

ELK
- Elastic search, Logstash and Kibana


#### Emacs workflow flor clojure 

* create a clojure project with leiningen 
* open either the project.clj file or src/test .clj file 
* with cursor in the .clj buffer, run M-x cider-jack-in or C-C C-j (my keybinding), actually ???


Thank you.
[@jr0cket](https://twitter.com/jr0cket)

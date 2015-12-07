title: "fullstack 2015 london - day 1"
date: 2015-10-26 08:37:59
categories: events
tags:
- javascript
---

Its the first day of [FullStack 2015](https://skillsmatter.com/conferences/6612-fullstack) at [SkillsMatter](https://skillsmatter.com), a chance to catch up with the international JavaScript community share skills with some of the world's top developers.

[TODO: Insert picture of conference crowd at skillsmatter]

Here are the talks I enjoyed, there are many more on the SkillsMatter skillscasts for #FullStackCon


## Keynote: The toxic side of free. Or: How I lost the love for my side project

Remy Sharp giving the trials & tribulations of running the JSBin service.

[JSBin](https://jsbin.com/) is a collaborative environment for JavaScript debugging.  It gives a live pastebin for HTML, CSS & JavaScript and a range of processors, including SCSS, CoffeeScript, Jade and more...


jsbin can lead to challenges of people spamming via jsbin, so added blocking based on IP addresses, however at conferences & workshops everyone has the same IP

Uses _204 no content_ when recieving requests for content that are not for a specific resource, this reduces a whole load of useless traffic as it can easily be handled by nginx rather than the application code.



has not been a great experience for him in the world of Open Source projects.  Unfortunately Remy is the sole contributor, so this can lead to a lot of work and lots of requests for features & bug fixes.  Why not give Remy a helping hand


Put a limit of 90 minutes for anonymous users.

Remy created a way for users to register on the site, so they could get their history.  However, as Remy added a basic


Bins take up disk space and even with 100GB it wasnt enough, even though all that is being written is text.  As Remy tried to clean up the disk space and make more room, more and more rows were being written to the database and therefore taking up more diskspace...

The moral of this story to my mind is to remove the free for all sign-in.  So you now have to register with Github, even though it may limit the number of people who can access JSBin




### How do we give you money

Remy didnt want money for JSBin, as at first he didint understand the value of money and the difference it could make to JSBin.  JSBin does not make a profit, far from it.  They get enough to cover server costs.  However Remy hired two great programmers

f
Charing pepole for a service costs money

vatmos - european union single digital market

because jsbin has a low cost of £6 also used as test bed for stolen cards, which cost me £21 via strike



## No real planning of marketing the service

No real marketing plan.  Assumed about 1% conversion rate from current level of users would cover for a full time developer.  However the conversion rate was more like 0.0.1%

I wished I had engaged with someone with experience in this matter.  Should have had a business plan and worked with someone who could understand the numbers.

If need is in the sencence then people will pay.


## Its the police

London metropolitain Police office has been used to co-ordinate an attack on a bank, they asked him to take down a few bins (it was a shock to get a call from the Met Police)


JSBin was also used for terrorism, so would you kindly take it down.  JSBin was used to attache the Maddison police department in the USA.  It was the Anonymous group that did the attach, they could have run their own JSBin service as its open source


As its free and open it allows anyone to use it, unfortunately this includes the few out there that use it for nafarious purposes.

Every new feature has to be reviewed to see if it will make any money





## Fully Reactive User Interfaces
Sébastien Cevey

Most traditional JavaScript is inherently imperative: for-loops, async callbacks, event listeners, DOM manipulations. By relying on side-effects, the resulting code is not composable, hard to test and reason about, and generally forgoes the power of functional programming. With this talk you will discover that it is not only possible to write a purely declarative user interface, but how much simpler the code reads as a result. In line with the 2015 trend of building on top of off-the-shelf libraries rather than large frameworks, it will solely rely on RxJS, virtual-dom and SystemJS.
javascript imperative declarative live-coding UI-RxJS virtual-dom SystemJS
About the speaker...
Sébastien Cevey

Sébastien Cevey is a software engineer at the Guardian where he leads the development of Grid, the new image management service. Before that, he was tech lead for Composer, the Guardian’s new digital-first CMS.

Editorial tools lie at the intersection of many of his interests, such as modelling semantic information and building elegant abstractions at all levels, from UX to API design.

Check out Guardian's developer blog here. '



## Reactive programming

express the logic of your app via ...

rxmarbles.com - reactive website


http://rxmarbles.com/





# The remarkable journey of a single web request
Aaron Kalin

How far would you have to travel to deliver just one request to a server when you type in their web address? You'll explore the journey a single request takes from the browser address bar, to the server, and back. You’ll discover just how many services, protocols, and systems are involved in delivering those oh so cute cat videos to your browser each day.
fullstack web-request fun web-technologies
About the speaker...
Aaron Kalin

Aaron Kalin is a System Administrator for DNSimple hailing from Chicago and has been programming for over 15 years. At night you'll find him hacking on game servers or experimenting with other programming languages. He's passionate about solving problems and enjoys giving back as much as possible.

Check out [DNSimple](https://dnsimple.com/).

.co.uk, org, com - top level domains

rubygems.org A IN

.org - top level domain
rubygems - domain
A -
IN - internet classification - chaos network(CN),

When you look up an address, it first looks in the local cache

if not, it looks in the stub resolver in your Operating system.

If your OS does not have it, then the lookup goes to the router which is either a DNS sever or points to a DNS server from your ISP.


User Datagram Protocol
- its really fast, no setup or tare down
- good for games and DNS servers

Transmission Control Protocol
- slower than UDP
- handshake overhead


## The Internet

So we have an address that we want to sent our packet to.  We open a socket and under the covers the OS is breaking down the packet into data and pushing it on to th enetwork card.

Your omputer opens a connection to the first step - probably the router (unless your computer is the router).  Where does the router send the packet too ??

Border Gateway Protocol
Lets ISP share routes information.  BGP builds this giant graph of a network.  There are several ISP's globally that have big bocks of addresses, so the router sends it to them.  Then it may be sent to another ISP, etc....


## The server
the server is sitting there listening for incoming requests, typically on 80 for HTTP traffic and 443 for secure traffic, eg, hTTPS



# Tessle 2

hardware should be easy for developers

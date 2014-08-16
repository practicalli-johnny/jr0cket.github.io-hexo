title: Netbeans and JUnit in Oracle land
date: 2011-02-21 01:34:00
categories: dev-tools
tags: 
- netbeans
- junit
---

{% img img-thumbnail http://netbeans.org/images_www/v5/nb-logo2.gif %}

It seems Oracle lawyers have advised the [Netbeans](http://www.netbeans.org) team that they can no longer ship [JUnit](http://junit.org) with the Netbeans IDE.  I originally did not understand this issue (see update below), but it seems that the Netbeans team have a neat way to deal with this "advice" anyway.

<!-- more -->

{% img img-code http://1.bp.blogspot.com/-iu6OYYxc2MU/TWG9N3mCuZI/AAAAAAAAARE/rLA-6BZUrrg/s1600/netbeans-7-beta2-Install-JUnit-Library.png %}

When you run Netbeans for the first time you are prompted to download JUnit testing library, as this is not distributed with Netbeans.

{% img img-code http://3.bp.blogspot.com/-Ev5VS5BOYs4/TWG_5oMYrHI/AAAAAAAAARI/551KIQaxESs/s1600/netbeans-junit-plugin-installer.png %}

Selecting OK will download the netbeans plug-in for JUnit and start the plug-in installer.

After accepting the JUnit 4 licence agreement, the install completes in a few seconds.  There is no need to restart the Netbeans IDE.

This approach with Netbeans and JUnit was experiences with Netbeans 7 beta 2, OpenJDK 6 and [Ubuntu](http://www.ubuntu.com) 10.10.

### Update from [Neil Bartlett](http://njbartlett.name/):

JUnit is still licensed under the [Common Public Licence](http://en.wikipedia.org/wiki/Common_Public_License) (CPL) which was superceded by the [Eclipse Public Licence](http://en.wikipedia.org/wiki/Eclipse_Public_License) (EPL) in many project. The only difference between CPL and EPL is this clause, which EPL removes:

> If Recipient institutes patent litigation against a Contributor with respect to a patent applicable to software (including a cross-claim or counterclaim in a lawsuit), then any patent licenses granted by that Contributor to such Recipient under this Agreement shall terminate as of the date such litigation is filed.

This clause leads to the possibility that if Oracle ever sues a contributor to JUnit for patent infringement, then all patent licenses granted to Oracle by that contributor could be revoked. 

Oracle have no such problem with the EPL software licence. NetBeans and many other Oracle products include parts licensed under EPL.

[According to Kent Beck](http://tech.groups.yahoo.com/group/junit/message/23147?var=1), if the CPL license is a big enough problem to get lawyers involved, then its an important enough reason to buy a commercial license.  Unless Oracle wants to pay for a commercial license, pay to get JUnit re-licensed or forget about suing anyone contributing to JUnit,  then I guess the Netbeans team will have to keep their work-around.

At least it seems that Netbeans 7 is back on track with JUnit and seems to be working well on OpenJDK, despite recommendations to only use the Oracle Java SDK.

Thank you.
[@jr0cket](https://twitter.com/jr0cket)

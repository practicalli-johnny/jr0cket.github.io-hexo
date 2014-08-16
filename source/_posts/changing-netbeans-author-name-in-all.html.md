title: Changing Netbeans Author name in all your templates
date: 2011-03-21 12:29:00
categories: dev-tools
tags: 
- netbeans
---

{% img img-thumbnail http://lh4.googleusercontent.com/-lwNcR4ID4SM/TYdA8fuTw2I/AAAAAAAAAUI/IK0etpwelRI/s1600/Netbeans-template-manger-user-properties.png %}

You can very easily get netbeans to use your full name when it generates code from it templates, rather than what ever you set your account name to be.

<!-- more -->

Open the menu item `Tools > Templates` to get a list of all the templates netbeans has.  At the bottom of this list is a folder called `User Configuration properties`.  Open the folder, select the `User.Properties` file and select the `Open in Editor` button.

Add your full name and email address in the example format shown in the file

    user=Your Name <your.name at your.org>

In my case I entered

    user=John Stevenson < john at jr0cket.com >

From now on, when you create a project your full name will be used for the author `@author John Stevenson < john at jr0cket.com >`

Thank you.
[@jr0cket](https://twitter.com/jr0cket)

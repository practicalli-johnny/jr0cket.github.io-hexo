title: Byobu saves the day
date: 2011-01-21 17:13:00
categories: dev-tools
tags: 
- ubuntu
---

{% img img-thumbnail http://a.fsdn.com/sd/topics/topicubuntu.png %} 

I took the bold (all right, crazy) decision to run with Ubuntu 11.04 whist still in heavy development directly on my Lenovo X201T tablet laptop, partly for the experience of the new Unity and Compiz desktop and partly to help with the testing.

As the 11.04 version of Ubuntu is still being written, I prepared myself to experience a few problems, but apart from one upgrade last Friday (my fault as I didnt look closely enough to see what `apt-get dist-install` was removing) I have been using Ubuntu 11.04 and Unity quite productively.

Occasionally I get the odd rendering problem with the menus when I login to a new Unity session, so I run the command `unity --reset` and all is well again.&nbsp; I leave the terminal window open to see if there are any useful error messages.

I did have a little bit of a crash today with Unity (core dump), but  as I also run byobu in my terminal window by default I was easily able to recover  without loosing any work or any windows or applications closing.

The unity core dump made my desktop unresponsive to keyboard, though I could still drop down to a virtual terminal (Ctrl-Alt-F1).&nbsp; When I logged into the virtual terminal, as byobu is set to run as default it picks up the same session I used to reset Unity and I see the core dump message.

So all I needed to do to get back to a working Unity desktop was issue the `unity --reset` command in the virtual terminal and jump back to my Unity desktop (Alt-F7).

So thanks [Byobu](https://launchpad.net/byobu), you have saved the day and I have found yet use for this great piece of software.

Thank you.
[@jr0cket](https://twitter.com/jr0cket)

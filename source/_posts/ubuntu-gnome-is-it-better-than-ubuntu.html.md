title: Ubuntu Gnome - is it better than Ubuntu?
date: 2013-10-14 23:17:00
categories: ubuntu 
tags: 
- ubuntu
---

{% img img-thumbnail http://www.gnome.org/wp-content/themes/gnome-grass/images/gnome-logo.png %}

With a new version of [Ubuntu](http://www.ubuntu.com/) this month, I asked myself if I would get more out of one of the many other Linux distributions.  Here is what I learnt.

<!-- more -->

I've used Ubuntu as my main Linux distribution since I changed from [Debian](http://www.debian.org/) in 2005.  I started using Debian in 1995, so if I did change distributions I wanted to stay with the _.deb_ packaging system which I value so much.  

Although I am weary of the reductions of features the Gnome team have made recently, [**Ubuntu Gnome**](http://ubuntugnome.org/) was the first alternative distribution I tried and was surprised to find I quite like it.

{% img img-code http://3.bp.blogspot.com/-jRj631yZJzY/UlsS3eLBbrI/AAAAAAAAL3U/FKLSLdKGn_I/s1600/ubuntu-gnome-my-basic-desktop.png %}

My Ubuntu Gnome desktop using Gnome Shell and a few extensions

## Installing Ubuntu Gnome
This is not any different from the normal Ubuntu install and everything went well on my Lenovo x201T.

I selected to install Ubuntu Gnome over the entire hard drive (SSD) and use an encrypted disk and LVM (just in case I want to re-organise partitions at a later date).  I chose to get updates and multi-media codecs (for playing music and videos) during the installation too.

After about 20-30 minutes I had a new OS for my laptop, all ready to use.  A quick reboot and within 10 seconds I am logging in to Ubuntu Gnome.

## First Impressions
Ubuntu Gnome uses Gnome shell and there is a lot of commonality between it and Ubuntu Unity desktop.  To my surprise though I found I quickly started liking Ubuntu Gnome for lots of little reasons.  It helped that I had a quick look at the [Gnome Shell cheat sheet](https://wiki.gnome.org/GnomeShell/CheatSheet) which gives a great overview of the main features.

## Performance
Gnome shell is really fast and responsive and I haven't had any slow-downs as I increase the amount of apps running. As Ubuntu Unity is pretty quick too, then I don't see any speed advantage.

Ubuntu Unity seems to use just a little bit more memory, but that may be due to more packages installed and extra services running (eg. UbuntuOne). Its not a significant difference.

### Automatic Virtual Desktops
Gnome shell automatically creates new virtual desktops as you add applications and deletes desktops when you close all apps on that desktop.  I like to keep one app per desktop, so its great that you can launch an app from the dash with the middle mouse button (the Lenovo laptops have 3 buttons) and it opens in a new desktop. When I close the app, Gnome shell tidies away my desktop, helping me keep more organised.  This is a feature I would love to have in Ubuntu.

Gnome Shell has vertically arranged desktops, so each desktop is stacked one on top of the other.     I quickly came to prefer this over the default grid of Ubuntu Unity.  Although you can change Unity's grid layout with Ubuntu Tweak, I haven't seen the ability to automatically create an delete desktops.

## The Dash
The Gnome Shell launcher similar to Ubuntu Unity, however in Gnome Shell its attached to the overlay rather than being their on the desktop.  So with Gnome shell I only see the launcher when I press the Super key (as I always run my apps maximised).  This keeps my desktop very simple.

Whilst the launcher in Ubuntu Unity has lots of great features to help you launch and switch to your apps, I found I didn't really use them.  I just set Unity to auto-hide the launcher 

## Notifications
Gnome shell displays notifications on the bottom of the desktop rather than the top right corner in Ubuntu Unity. I prefer the placement in Ubuntu Unity, although they both could be smaller so they are less intrusive.

## Unwanted software
There were a few packages and services that came with Ubuntu Gnome I didnt require, but not many.  The main packages I removed were:

* epiphany - an messaging client (I use Google for that)
* spamassassin - email spam service (again I use Google)

To remove the packages I just used the command line, as I knew the specific package names it was quicker than launching the Ubuntu software center

    apt-get remove --purge package-name

To find out if there were any services running that I didnt need I use the command line again to list the status of all services currently installed:

    sudo service --status-all

From this command I discovered spam assassin and removed it as above.

## [Gnome Shell Extensions](https://extensions.gnome.org/)

Gnome Shell allows customisations via extensions (written in JavaScript and possibly other languages) and there is [a website full of them](https://extensions.gnome.org/).  The Gnome Shell extensions are really easy to use, its just like using the Chrome or Firefox extensions.

Each extension on the website has an on/off switch.  Switching on prompts you to accept that the package will be installed.  For some extensions there is also a tool icon that you can press to configure the extensions once installed.  You can manage your installed extensions from [https://extensions.gnome.org/local/](https://extensions.gnome.org/local/).

These extensions give a really easy way to add features and Gnome Shell and without them it would have diminished the experience amd I would have stopped using Gnome Shell then and there.

The only issue with these extensions is that they can become outdated and break, with each release of Gnome Shell.

### Extensions added
**AppIndicator Status**

I use Dropbox to sync important files between different laptops (Linux, Mac) and although its easy to install Dropbox in Ubuntu Gnome, the status panel indicator for dropbox does not display.  By adding AppIndicator extension then the dropbox icon appears and I can control syncing of my files again.

**[Media Player Indicator](https://extensions.gnome.org/extension/55/media-player-indicator/)**

In Ubuntu Unity you can start and control the default music player (Rhythmbox) from the volume indicator.  The Media Player Indicator adds that functionality in Gnome Shell.  It worked for Rhythmbox although the Playlists didnt show up in the volume indicator.

** [Hide Top bar](https://extensions.gnome.org/extension/545/hide-top-bar/)**

The biggest thing that put me off Gnome Shell at first was the wasted space at the top of the screen.  First there is the Gnome Shell menu bar, then the window decoration for the application, then the application menu and then the content of the app. From what I have read (cheat sheet) Gnome Shell will go the same route as Ubuntu Unity and put app menus in the top panel, making better use of the space.  Until then, I find [Hide Tob Bar](https://extensions.gnome.org/extension/545/hide-top-bar/) very welcome.  I have it set to auto hide and only show when the mouse approaches it.

**[EasyScreenCast](https://extensions.gnome.org/extension/690/easyscreencast/)**

Gnome Shell as screen casting software built in so you can record your desktop using `Control+Shift+Alt+R`.  Rather than have to remember that keyboard combo, EasyScreenCast gives you and indicator to control the recording.

EasyScreenCast seems to work really well and uses the [webm codec](http://www.webmproject.org/) by default, so you can just upload that straight to YouTube.

### Extensions to look at later

[Fast user switch](https://extensions.gnome.org/extension/719/fast-user-switch/) - enables you to switch users without having to go via gdm

[Task bar](https://extensions.gnome.org/extension/584/taskbar/) - displays icons of running applications on the top panel.  If I run more than one app per desktop this may be useful.

[Uptime indicator](https://extensions.gnome.org/extension/508/uptime-indicator/) - shows how long in minutes it has been since the last boot.  Clicking on the indicator shows you the time Ubuntu Gnome was started.

[Pomodoro time](https://extensions.gnome.org/extension/53/pomodoro/) - gives you a countdown to timebox work into 25 minute sessions. This pomodoro technique helps you concentrate on one task and get it done well.

[Monitor status indicator](https://extensions.gnome.org/extension/11/monitor-status-indicator/) - a short-cut for the display controls to quickly manage your display settings.  I had a few problems with a second monitor, not sure if its this extension of Gnome Shell.

## Summary
I like Ubuntu Gnome and Gnome Shell enough to give it a try for a few more weeks until the final versions of [Ubuntu](http://www.ubuntu.com/) and [Ubuntu Gnome](http://ubuntugnome.org/) are released. My Lenovo X201T is my spare laptop, so it doesn't matter if something breaks, I can still do work on my my Lenovo X1 carbon, running Ubuntu.

Things in Ubuntu Gnome are changing quite a bit and there is a tendency for Gnome Shell extensions to break with new releases.  To see what is coming next have a look at the [Gnome 3.10 features and changes](http://www.omgubuntu.co.uk/2013/09/10-best-features-gnome-3-10).

One thing that may make a difference is that both distributions will be replacing X windows.  Ubuntu has created [Mir](https://wiki.ubuntu.com/Mir/) and the Gnome project is behind [Wayland](https://wiki.gnome.org/Wayland).  Its going to be interesting to see which approach works out best over the next few releases.

{% blockquote %}
I did try [Arch Linux](https://www.archlinux.org/) for a weekend and although there are some great things with the distribution, for now it just seems to eat too much time in setting everything up and learning the different tooling.  Although there is a lot of documentation, I found myself having to read pages and pages of content and not always finding the answers I was looking for.
{% endblockquote %}

## 6 month later

I am still using Ubuntu as my prefered Linux distribution.  Gnome Shell has still a long way to come to offer the features I need and the extensions I want to use break to often to be fun fixing.

When Gnome Shell becomes more evolved and incorporates Wayland, then it will be time to give it another try and see how it stacks up to Ubuntu, Unity and Mir.

Thank you.
[@jr0cket](https://twitter.com/jr0cket)


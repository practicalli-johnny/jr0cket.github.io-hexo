title: Trying out Ubuntu 11.04 on Lenovo X201T
date: 2010-12-14 10:53:00
categories: ubuntu
tags: 
- ubuntu
- lenovo
---

{% img img-thumbnail http://static.arstechnica.com/unity-multi-selector.png %}

I am vastly more productive when I use Ubuntu as an Operating System as it is fast and gives me all the tools I need to get things done.  Unfortunately Lenovo dont support me in this requirement, shipping Windows with theiir products.  So to replace the incumbant Microsoft Windows software on my Lenovo Thinkpad X201T tablet, I intend to replace the 320GB hard disk with an [OCZ Vertex 2E 128Gb solid state drive](http://www.ebuyer.com/product/225416) (SSD).  The Lenovo lets you easily swap out the hard drive (great design).  This way I can simply put the original hard drive back in should I decide to sell the laptop.  Here is my approach.

<!-- more -->

Whilst I wait for the [OCZ SSD from ebuyer](http://www.ebuyer.com/product/225416), I am running [Ubuntu](http://www.ubuntu.com) 11.04 from a nice and speedy SanDisk Cruzer 4Gb USB memory stick.

I downloaded the [64-bit PC (AMD64) desktop CD alpha1 ISO image of Ubuntu 11.04](http://cdimage.ubuntu.com/releases/11.04/alpha-1/natty-desktop-amd64.iso) and used my Ubuntu 10.10 laptop to create a USB startup disk (Ubuntu live) on the first USB memory stick.

Plugging in the first USB stick into one of the three USB ports on the Lenovo x201, I powered on and at the ThinkPad splashscreen pressed the F12 key to get the boot menu.  Selecting the Scandisk USB device, the laptop started to boot Ubuntu live.

{% blockquote %}
Tip: When you see a purple screen with a picture of a white matchstick man and a keyboard, if you press select you can save yourself quite a few seconds of boot up time by using the basic menu to decide if you want to run Ubuntu Live or run an install.
{% endblockquote %}

Plugging in a second Scandisk USB stick I am going to use to install Ubuntu onto, I select the Install Ubuntu option.  Following the default install options until I get to choose where to install Ubuntu, I selected to choose manual partition selection.

At the bottom of the list was `/dev/sdc1` which represented the second USB stick I insterted.  The usb stick you are running the installation from will not show up in the list of devices to stop you from installing there.

To install on the second USB I select `/dev/sdc1` and hit the change button.  Selecting `EXT4` as the partition type, using the full size of the USB stick, selecting to format the partition and selecting `/` (root) as the partition mount point.

When selecting okay, the option as to where the Grub boot loader changes to the second USB stick, `/dev/sdc`, which is what I want in order to use the USB stick on any laptop.

The rest of the install should be just clicking forward while all the files are copied across to the second USB stick, `/dev/sdc` SanDisk Cruzer Blade(4.0 GB).  As I connected my laptop to the wired network, Ubuntu worked out my location correctly and gave me decent settings for my keyboard automatically.

The first boot from the new USB stick install did take about 45 seconds to start up, but subsequent boots are pretty quick and less than 25 seconds usually.

Unity desktop is shaping up quite nicely and is very very fast, I mean really fast.  Amazing since its loading software from the USB memory stick.

Try out [Ubuntu](http://www.ubuntu.com) for yourself, its very easy.

Thank you.
[@jr0cket](https://twitter.com/jr0cket)

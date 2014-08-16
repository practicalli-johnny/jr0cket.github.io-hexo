title: Virtualbox Guest Editions for Ubuntu
date: 2011-03-01 12:00:00
categories: ubuntu
tags: 
- ubuntu
---

{% img img-thumbnail http://upload.wikimedia.org/wikipedia/en/d/d5/Virtualbox_logo.png %}

Using Virtualbox is a way to run an isolated environment on your desktop and help manage a consistent deployment process.  To have Virtualbox running efficiently on Ubuntu you really should install the utilities and drivers that come in the Virtualbox Guest Editions addon.

<!-- more -->

After you have installed your Linux Guest system, there are a few additional packages needed for the Guest Additions. These packages enables you to create specific kernel modules for Virtualbox on your Ubuntu virtual server.&nbsp; For Debian based distro's like Ubuntu, you need to install the following packages or the installation of the guest additions will fail:

    dkms
    build-essential
    linux-headers-generic

In a terminal window, you can use the following command to install the neccesary packages

    sudo apt-get install dkms build-essential linux-headers-generic

# Mounting the guest editions with Ubuntu 10.10 (host &amp; guest) with virtualbox 4

Using the virtualbox menu to mount the VirtualboxGuestEditions.iso image file is problematic.&nbsp; Just selecting the iso from the _Devices &gt; CD/DVD Devices_ is not sufficient to get the image to mount.

{% img http://lh5.googleusercontent.com/-6uGwUDgf5lw/TXjjP5bJvGI/AAAAAAAAASg/orOYA3UiEQ0/s1600/Virtualbox4-GuestEditions-menu.png %}

First you should unmount any other iso images, especially the Ubuntu server install image.  Then run the following command to mount the guest editions image

    sudo mount /dev/scd0 /media/cdrom
    
Followed by selecting _Devices &gt; CD/DVD Devices &gt; VBoxGuestAdditions.iso_ from the virtualbox menu

This will then complete the mount command issued previously and you then have access to the mounted cd image.

Run the guest editions installer using the following command

    sudo /media/cdrom/VBoxLinuxAdditions.run

Now that we have what is needed for the Guest Additions, it's time to actually start installing what we want. If you haven't done so already, mount the GA ISO to the VM. This is done using the Device Menu, then click on Install Guest Additions. See the screen shot.

Make sure that no other CD is already loaded for the VM, like the install disk. Unmount that one first. The CD doesn't always get mounted automatically, so you have to do that manually. Usually an icon appears on the Desktop with the name of the inserted CD. You can mount the disc from there, but if you don't have a GUI, you have to mount it using the command line. The CLI can also be used if you have a GUI. Use a terminal emulator for that.

On the command line, check if there is a valid mount point for the CD. This is usually `/media/cdrom`, but any empty folder can be used as mount point. Now to mount the CD, issue the following command:

    mount /dev/scd0 /media/cdrom
    
{% img http://lh3.googleusercontent.com/-3_FSEPKHWF8/TW0aBjkP5uI/AAAAAAAAARw/Ph3zbPg9nsE/s1600/VirtualBox-guest-edition-install-server.png %}

# Using Usb and shares

There is a good guide to using USB memory sticks and drive shares at:

http://blog.eviac.com/2010/07/oracle-virtualbox-tips.html

For more configuration ideas, have a look at the [virtualbox forum](http://forums.virtualbox.org/viewtopic.php?f=3&amp;t=15679)
 
Thank you.
[@jr0cket](https://twitter.com/jr0cket)

title: Ubuntu on Lenovo X1 Carbon - Tweaking the bios and added security
date: 2013-03-15 18:00:00
categories: ubuntu
tags: 
- lenovo
- ubuntu
---

{% img img-thumbnail http://3.bp.blogspot.com/-mIMpXCWQUw4/UUJJ1R0pADI/AAAAAAAAJKA/-3aHKq5wJwc/s1600/lenovo-carbon1.jpg %} 

I have a lovely new Lenovo X1 Carbon and to make it even better I am installing [Ubuntu](http://www.ubuntu.com).  The installation should be a breeze as Lenovo laptops are usually well supported, the only thing I configured was in the BIOS.  I wanted to check the boot order and see what the boot menu key was so I could install Ubuntu from a USB memory stick (boot menu key is F12).

<!-- more -->

Pressing the little "Thinkpad" button next to the volume controls whist the laptop is first booting gives you an option to go into the bios. 

## Secure Boot and the boot order 

Once the BIOS control panel had loaded up, In the overview section I noticed that Secure Boot was enabled.  So I looked through all the sections and found an option to turn it off.  I also changed the boot order so that USB memory sticks can be used to boot from.  Saving the changes rebooted the machine and I pressed F12 on restart to select the USB stick I had created for the Ubuntu installation.

Apart from thinking of a good name for my new laptop, the install was really easy.  I decided to use the whole hard drive (SSD) space for Ubuntu and ditch windows 8 completely.  There were 3 recovery partitions that come with the laptop if I wanted to keep windows for a later date.  I did not.

{% img img-code http://3.bp.blogspot.com/-i09UXqkk_3E/UUMtyYQNciI/AAAAAAAAJKc/N1oz7QeNT5E/s1600/ubuntu-install-cfdisk.png %}

*Disk partition information from: sudo cfdisk*

## Added security and partition flexibility 

I decided to encrypt the whole laptop and this works really well.  For the rare occasion I shut down or restart the laptop, I get prompted as Ubuntu starts up to enter the password to unlock the encrypt drive.

I also decided to install Logical Volume Managment (LVM), just in case I needed to play around with the partition sizes.  As I have a 180GB SSD hard drive, I probably wont need to but it should not add a noticeable overhead.

One thing that is missing is a swap partition, but the only upshot of this on a laptop with 8GB is that hibernate has knowhere to write to, so its currently disabled.  I'll probably manually partition the laptop when Ubuntu 13.04 comes out (25th April).

To finish off the install I just chose a name for the laptop and the usual username/password and everything was done in less than 30 minutes. I didn’t need to do anything to boot into the installed version of Ubuntu.

Next I'll check out how well sound and video works.

Thank you.
[@jr0cket](https://twitter.com/jr0cket)

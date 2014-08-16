title: Testing upcoming release of Ubuntu with TestDrive
date: 2010-08-22 17:48:00
categories: ubuntu
tags: 
- ubuntu
---

{% blockquote %}
[Launchpad](https://launchpad.net/testdrive) | [GUI](https://blueprints.launchpad.net/ubuntu/+spec/desktop-maverick-testdrive-frontend-gsoc) | [Introducing](http://blog.dustinkirkland.com/2009/11/introducing-testdrive.html) | [TestDrive Lucid](http://blog.dustinkirkland.com/2010/02/have-you-taken-lucid-for-testrive-yet.html) |
{% endblockquote %}

{% img img-thumbnail http://wiki.ubuntu.com/Testing?action=AttachFile&amp;do=get&amp;target=flask192x192.png %}

One of the easiest ways to get involved with testing a new release of Ubuntu is to use TestDrive.  TestDrive makes it very easy to download and run the latest daily Ubuntu development snapshot in a virtual machine&nbsp; (KVM, Virtualbox, etc.) without affecting the rest of your system.

Actually, TestDrive can be configured to download and run any URL-accessable ISO image in a virtual machine, although the primary goal is to provide feedback on the current Ubuntu release under development.  Here is how to get going with TestDrive.

<!-- more -->

If you are running Ubuntu 10.04 (Lucid Lynx) you can install TestDrive package using your favourite package manager, or by using the following command:

    sudo apt-get install testdrive

For older versions of Ubuntu, there is a personal package archive, which can be added using the following commands:

    sudo add-apt-repository ppa:testdrive/ppa
    sudo apt-get update &amp;&amp; sudo apt-get install testdrive


## Change the TestDrive configuration

If you need to change the configuration of TestDrive, you can create your own configuration file

    gedit ~/.testdriverc

or edit the global configuration file

    gksudo gedit /etc/testdriverc

No changes are required unless you want to use a virtual machine other than KVM.

## Running TestDrive

TestDrive is available from the menu Applications > System Tools > Testdrive or by running the command `testdrive`.

After some checks you will be presented with a simple menu, where you choose which version of Ubuntu you wish to run (configurable in the TestDrive configuration file).  Once you have chosen the version of Ubuntu to run, TestDrive will download the image (or update any existing images you have) and run that image as a virtual machine.

    ~$ testdrive 
    INFO: version passed: False
    INFO: config passed: None
    INFO: Trying config in /etc/testdriverc
    INFO: Using configuration in /etc/testdriverc
    INFO: Trying config in /home/johnny/.testdriverc
    INFO: Trying config in /home/johnny/.config/testdrive/testdriverc
    INFO: Using KVM for virtual machine hosting...
    INFO: Retrieving the Ubuntu ISO list from cache...

    Welcome to Testdrive!

     1\. Ubuntu Desktop (maverick-amd64)
     2\. Ubuntu Desktop (maverick-i386)
     3\. Ubuntu Alternate (maverick-amd64)
     4\. Ubuntu Alternate (maverick-i386)
     5\. Ubuntu DVD (maverick-amd64)
     6\. Ubuntu DVD (maverick-i386)
     7\. Ubuntu Netbook (maverick-i386)
                 +-cache--&gt; [2010-08-22 03:11:54] maverick-netbook-i386.iso
     8\. Ubuntu Server (maverick-amd64)
     9\. Ubuntu Server (maverick-i386)
     10\. Other (prompt for ISO URL)

    Select an image to testdrive [1]: 7
    INFO: Syncing the specified ISO...
                     rsync://cdimage.ubuntu.com/cdimage/ubuntu-netbook/daily-live/current/maverick-netbook-i386.iso
    receiving file list ... 
    1 file to consider

    sent 139 bytes     received 100 bytes     478.00 bytes/sec
    total size is 768491520     speedup is 3215445.69
    INFO: Validating Virtualization Method....
    INFO: Setting up Virtual Machine...
    Creating disk image [/opt/ubuntu/cache/img/testdrive-disk-4HKyYB.img]...
    Formatting '/opt/ubuntu/cache/img/testdrive-disk-4HKyYB.img', fmt=qcow2 size=6442450944 encryption=off cluster_size=0 
    INFO: Launching Virtual Machine...
    Running the Virtual Machine...`

You should now have a running version of Ubuntu in a virtual machine, so you can try it out in safety and report any bugs you find to help with the next Ubuntu release.

Thank you.
[@jr0cket](https://twitter.com/jr0cket)

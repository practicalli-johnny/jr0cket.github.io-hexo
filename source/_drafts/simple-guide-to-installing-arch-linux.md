title: Simple Guide to Installing Arch Linux
tags:
---

  Arch Linux promises a completely customised Linux experience.  As I am always on the move and doing lots of different tasks, having a lightweight OS with low memory and power usage is invaluable.
  
  Arch Linux can give you this, however it will take much longer than other Linux distributions to get going.  So is it worth it?
  
> After spending over 6 hours setting Arch Linux up on one laptop (and making notes on all the issues I had so I can repeat the process), I am still not sure if Arch Linux is worth the time it takes to set it up.

> Using distributions such as, [SparkyLinux](),  ... and [ArchBang]() should take the away some of time & pain of installing Arch Linux. 

<!-- more -->

## How big are Linux distributions
  
  Out of the box Linux distributions such as Ubuntu are great if you just want to get on with work (or play), you can be up an running in 30 minutes.  However, the memory use of Ubuntu and Gnome Ubuntu is very high at around 1.8Gb when logged in.

  Lighter weight distributions such as Lubuntu of Xubuntu still used around 800Mb of memory.  I find the user experience very dated, compated to Ubuntu Unity or Gnome Shell, the blocker for me is their desktop environments are not keyboard driven.
  
  With Arch Linux and Enlightenment desktop I get a very lightweight OS, using around 400Mb.  As I am also running fewer services, the OS should use less power too (although this needs to be tested in more depth).

## Create a USB stick installer

  Get a USB stick of at least xGb's  (if you have USB3.0 ports, make sure its a fairly recent USB stick - I had some old ones that didnt work, although that could be due to age)
  
  Download the ArchLinux image from archlinux
  
  dd if=archlinux.xx. of=/dev/sdx

> It will take up to 5 minutes to copy the arch linux image on the USB stick, so time for a read of the Arch Linux docs...

  Restart your computer.  Use the key that allows you to select boot priority, `eg, F12`, or configure your computer BIOS to boot from the USB stick first.

## Preparing to install Arch Linux 

 With Arch Linux running on your computer from your USB stick, you can set up your computer to install Arch Linux.

**Setup the keyboard**

  I have a UK keyboard layout and by default Arch Linux uses a US layout.  So, by looking at the keyboard layouts available with `localectl list-keymaps` I discovered the `uk` keyboard map.  I set this with
  
  loadkeys uk

**Selecting a bigger font**

    setfont sun12x22


> Note that the keyboard map names are case sensitive
 
**Test your network**

    ping www.google.com 

> Use Ctrl-c to stop this command.

  You should see several lines, at the end of each its telling you in milliseconds how long it took to recieve a successful ping.  If you get time-outs, then your network is not working.
  
> On the Lenovo X1 Carbon (3rd Gen) laptop, I used the network dongle that it comes with.  This dongle uses a propriatary port, rather than a USB port, so its something else to carry around.

**Setup your wifi**

  If you have a password on your wifi network, they you will need to configure the wifi network using `wifi-menu`

  You should be prompted with a dialog listing all the networks discovered. Select one and when prompted, enter the Wifi network password.

> This worked correctly on the Lenovo

**Partitioning your hard drive**

  You can use `parted` or `gpart`, but I still prefer the classic `cfdisk` as its really easy to use.
  
  I deleted all the existing partitions and created two new single partition:
  
  /dev/sda1 - 250M - this will be the boot partition which will remain unencrypted 
  /dev/sda2 - 238.2G - is the rest of the hard drive space which will make up / (root) and be encrypted

  Write the partition changes to disk and then quit
  
**Creating the file system**

  On each partition you created, you need to add a file system.  The `ext4` file system is recommended.
  
    mkfs.ext4 /dev/sdx

  In this case, as I have two partitions, I run the following commands
  
    mkfs.ext4 /dev/sda1
    ;; mkfs.ext4 /dev/sda2  -- not this partition, as we are going to encrypt it first


**Encrypting the root partition**

https://wiki.archlinux.org/index.php/Dm-crypt/Encrypting_an_entire_system


  Format the root partition and add a password for the encryption, you are prompted for a key (which you will need to type each time you do a reboot of Arch Linux)
  
    cryptsetup -y -v luksFormat /dev/sda2

  This creates an encrypted container over the partion that must be unlocked, so lets unlock it with the password we just used.  

    cryptsetup open /dev/sda2 cryptroot

Then we can format the container with a file system

    mkfs.ext4 /dev/mapper/cryptroot
    
**Mount the new filesystem**

  As I have a seperate boot partition, I first need to mount the root partition, then mount the boot partition inside the root partition.

  First lets mount the root partition as /mnt (it cant be root just yet as we are using that for the installer)

    mount -t ext4 /dev/mapper/cryptroot /mnt

  Then I make a folder to inside the mounted root partition and mount the boot partition inside root
  
    mkdir /mnt/boot
    mount /dev/sda1 /mnt/boot

 
**Configure where to get Arch Linux packages**

  Arch Linux is made up of thousands of packages, any of which can be added and upgraded via one of many servers on the Internet.  So lets add a server near to our location by editing the packages mirror list
  
    nano /etc/pacman.d/mirrorlist 

> This list can be refined once Arch Linux is installed, using the [Packman package mirrorlist generator](https://www.archlinux.org/mirrorlist/), where you can select your country and it returns the list of all the mirrors.

## Installing Arch Linux 

**Install just the basics into the new root partition**

    pacstrap /mnt base base-devel

> Arch Linux will now install on your computer, so sit back and relax for a minute or two.

**Create a filesystem list for booting**

    genfstab -U -p /mnt >> /mnt/etc/fstab
    nano /mnt/etc/fstab
    
> Edit the fstab file to ensure it generated correctly, if it is not right then edit the fstab file

> I change the relatime mount option to noatime for both partitions, as I do not need timestamps updated each time I read a file.  See https://wiki.archlinux.org/index.php/fstab (at the bottom) 

**Adding encrypt to ramdisk creation**

mkinitcpio is a Bash script used to create an initial ramdisk environment.  We need to edit the configuration of this script to include encrypt

    nano /mnt/etc/mkinitcpio.conf

  At the bottom of the HOOKS section, one line is uncommented (no #), add the text `encrypt` before the text `filesystems` on this line.  Then save the file.

> See https://wiki.archlinux.org/index.php/Dm-crypt/System_configuration#mkinitcpio


## Configure Arch Linux basics

  Lets mount the new operating system create and configure a few defaults 
  
  Change root into the new system:
    arch-chroot /mnt

Set the hostname:
    echo whtestar2 > /etc/hostname

Set the time zone:
    ln -sf /usr/share/zoneinfo/Europe/London /etc/localtime



**Locale**

  Unconmment the locale you want in

    nano /etc/locale.gen

  Then generate those locales
  
    locale-gen

> For the UK locale, I used `en_GB.UTF-8 UTF-8`
  
  Create a locale configuration file:
  
    echo LANG=en_GB.UTF-8 > /etc/locale.conf

  Set the locale while we finish off the configuration

    export LANG=en_GB.UTF-8 


**keymaps** 

    nano /etc/vconsole.conf 
    
    KEYMAP=uk
    
**timezone** 

  Set the timezone to use for Arch Linux 
    ln -s /usr/share/zoneinfo/Europe/London /etc/localtime

  Set the hardware clock to UTC
    hwclock --systohc --utc

> May not need this if you only run one operating system, it didnt work on 3rd gen laptop


**set the hostname**

  Set the name for your computer 

    echo myhostname > /etc/hostname

> where `myhostname` is the name you want to call your computer

  Add your hostname to the hosts configuration 
  
    nano /etc/hosts 
    
  Add your hostname to the end of each line


**set up the network**

  Using dhcp (use connman later) to set up a dynamic ip address for a wired (eth0) connection.
  
  As Arch Linux now uses system.d, you need to discover the name of your ethernet connection.  The previous naming convention of `eth0` no longer works.
  
  To find the name of your ethernet connection, use the command `ip link`
  
  Entry **1:** will be the loopback address, entry **2:** will be the name of the ethernet connection
  
    systemctl enable dhcpcd@enp0s25.service


**Set a password for root user**

    passwd

**Setup a boot loader**

  So you can boot into Linux...
  
    pacman -S grub 


Configuring the boot loader
In order unlock the encrypted root partition at boot, the following kernel parameters need to be set by the boot loader:

    nano /etc/default/grub

  Add the following to the `GRUB_CMDLINE_LINUX_DEFAULT` option
    cryptdevice=/dev/UUID root=/dev/mapper/cryptroot


    grub-install --target=i386-pc --recheck /dev/sda
    grub-mkconfig -o /boot/grub/grub.cfg


    exit 
    reboot 




  Now you are ready to see if it all works.  Once the arch linux installer has shut down, remove the usb stick and watch Arch Linux boot up on your computer.  

## Post install 

**what, no network**

> I updated the guide to fix this issue, if you still have problems with network connection then read on.

  On Arch Linux booting up, there was no network connection.  However, by running the `dhcpcd` command, I get a network. 
  
  As Arch Linux now uses system.d approch, the previous naming convention of `eth0` no longer works.  

  Run the command `ip link` and find out the name of your ethernet connection.  Then run the following command with this name

    systemctl enable dhcpcd@enp0s25.service    

> substitute `enp0s25` with the name of your ethernet connection

**Install zsh**

  I love zsh, so lets change to it from bash and set zsh as the default for the normal user we will create later.

  update pacman 
    
    
  install zsh 
    pacman -S zsh

**setting up a user**

  Set up a new user using zsh and with sudo access for adding software to Arch Linux and other admin tasks.
  
    useradd -m -G wheel -s /bin/zsh jr0cket


> The wheel group - Administration group, commonly used to give access to the sudo and su utilities (neither uses it by default, configurable in /etc/pam.d/su and /etc/pam.d/su-l). It can also be used to gain full read access to journal files.

  Then set the password for that user account 
  
    passwd jr0cket


  Finally, update the sudo list so that the wheel group is authorised to run administrative tasks 
  
    visudo 
    
  Find the line `# %wheel ALL=(ALL) ALL` and uncomment it by deleting the `#` character as the start of the line


## X and Destop managers

  While I wait for Wayland or Mir, I need X to run a graphical environment for apps like Chrome or Firefox.

**Adding an X Server**
  
    pacman -S xorg-server
  
    pacman -S xorg-xinit 
  
**Desktop Manager - Enlightenment**

  I wanted a desktop manager that uses very little resources, both in terms of memory and power (especially power).  
  
  As I will be using the desktop all day, every day, then I want something that I enjoy working with.  I am a keyboard junkie, so something I can drive all through the keyboard is ideal.  So it needs to do both of these things out of the box or be configurable to do so.
  
  I like Ubuntu Unity, although Ubuntu does take about 1.8Gb memory when running.  The same for Gnome Shell.  KDE looks very slick these days, but still has the heavyweight memory use if I want it to look like something other than windows.
  
  Most of the lightweight window managers are very basic and not that keyboard driven.
  
  So my current faviorite is Enlightenment.  This desktop environment has been around longer than Gnome and KDE.


    pacman -S enlightment

    pacman -S connman 
    
> not sure if this is needed as network manager seemed to be running - unless connman looks the same as network manager.
    
    

## To use a Display manager

  Display managers provide a graphical way to login to you computer.  All the major distros have nice screens to use, but I cant help think that this is really redundance for me.
  
  I am the only one who uses my laptop and I can set the destop to start automatically as I login on the command line.  I am not sure how much resources this will save, but I assume the display manager is running in the background so its there when you logout.
  
  

title: Cloning a Virutalbox 4 virtual machine
date: 2011-03-14 11:25:00
categories: dev-tools
tags: 
- virtualbox
---

{% img img-thumbnail http://www.virtualbox.org/graphics/vbox_logo2_gradient.png %} 

Cloning an existing virtual machine is not an obvious part of the VirtualBox user interface, even in version 4 of Virtualbox.  You have three options as far as I can tell

1) Export an existing virtual machine and import as a new machine
2) Create a new virtual machine using a cloned hard drive file
3) Create a new virtual machine using a copied hard drive file with a changed unique identification number (not official supported)

<!-- more -->

# Export / Import a virtual machine

{% img img-code http://lh4.googleusercontent.com/-bP0m9Yy-0Dw/TXuHQOKUohI/AAAAAAAAASk/V55bs7Xjk7s/s1600/Virtualbox4-ApplianceExport-Format.png 

You can export a virtual machine and then import it back as a clone, this is probably the easiest way to create an exact clone.  You  are able to change a few details regarding the virtual machine,  especially on import

{% img img-code http://lh5.googleusercontent.com/-3QFr08zKs_o/TXudkHiZY6I/AAAAAAAAASo/FLOWsKacDSM/s1600/VirtualBox4-Appliance-Import-Settings.png %}

Your new virtual machine hard drive will use the `.vmdk` file format, but everything else should be the same.

> I would be interested to know if there are any limitations / issues using a .vmdk file for a hard drive over the VirtualBox .vdi file format.

Outstanding question: How does this process handle snap-shots???

# Clone just the hard drive

You can clone just the hard drive of an existing machine using the Virtualbox command line tool - [VBoxManger clonehd](http://www.virtualbox.org/manual/ch08.html#vboxmanage-clonevdi).  When you create a new virtual machine you can use the cloned hard drive as the hard drive for the new virtual machine, saving you a reinstall.

You cannot simply copy all the files of an existing as each machines  hard drive uses a unique identification number.  The identification  number is spread through the virtualbox machines xml configuration  files, so updating it can be problematic.

The hard drive is the file inside your virtual machine directory with the .vdi file extension.

## Cloning an existing machines hard drive - supported method

1) Merge any existing snapshots into the main hard drive

2) Turn the virtual machine off

3) Run the [**VboxManager clonehd**](http://www.virtualbox.org/manual/ch08.html#vboxmanage-clonevdi) command "hard-drive.vbox" "hard-drive-cloned.vbox"

    VBoxManage clonehd ~/VirtualBox\ VMs/Ubuntu\ Server\ 32bit/Ubuntu\ Server\ 32bit.vdi  ~/VirtualBox\ VMs/Ubuntu-Server-32bit-base.vdi

    ~/VirtualBox VMs/Ubuntu Server 32bit$ VBoxManage clonehd Ubuntu\ Server\ 32bit.vdi Ubuntu-Server-32bit-base2.vbox
    0%...10%...20%...30%...40%...50%...60%...70%...80%...90%...100%
    Clone hard disk created in format 'VDI'. UUID: c90c5698-cf88-4452-849d-70ee6f950d13
    
Full path to files is not required, at least on Ubuntu Linux host, but may be necessary on other operating systems.

Refering to the hard drive meta-data, the .vbox file, will cause the command to fail.  Virtualbox need to know the file name of the hard drive you want to clone, so use the .vdi file.  If you refer to the .vbox file you will get the following error:

    ~/VirtualBox VMs/Ubuntu Server 32bit$ VBoxManage clonehd Ubuntu\ Server\ 32bit.vbox Ubuntu-Server-32bit-base3.vbox
    VBoxManage: error: Could not get the storage format of the medium '/home/johnny/VirtualBox VMs/Ubuntu Server 32bit/Ubuntu Server 32bit.vbox' (VERR_NOT_SUPPORTED)
    VBoxManage: error: Details: code VBOX_E_IPRT_ERROR (0x80bb0005), component Medium, interface IMedium, callee nsISupports
    Context: "OpenMedium(Bstr(pszFilenameOrUuid).raw(), enmDevType, AccessMode_ReadWrite, pMedium.asOutParam())" at line 209 of file VBoxManageDisk.cpp

4) Create a new virtual machine and use the cloned hard drive instead of creating a new one.

## Copy a Hard drive and change the ID (Unsupported internals alternative)

There is an unsupported internal function of the VboxManger command called sethduuid.  This will generate a new identification number for a hard drive.

So, if you copy the hard drive file and then run the following command on the copied hard drive file, you should be able to use that hard drive in a new virtual machine.

    VboxManager internalcommands sethduuid “cloned-hd.vbox”

# Final thoughts

I manly use VirtualBox for Ubuntu server virtual machines and its often less fiddly just to create a new virtual machine from the Ubuntu server image (.iso) file.  I have found that installing guest editions can be a little strange in Ubuntu server, so I am writing a guide to help.

See the [VirtualBox manual](http://www.virtualbox.org/manual/) for more information about VirtualBox configurations.

Thank you.
[@jr0cket](https://twitter.com/jr0cket)

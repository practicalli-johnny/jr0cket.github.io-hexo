title: Ubuntu 10.10 hibernate suspend bug fix - only for some laptops
date: 2010-10-23 14:20:00
categories: ubuntu 
tags: 
- ubuntu
---

I am really enjoying the new version of [Ubuntu](http://www.ubuntu.com), 10.10 Maverick Meerkat.  I especially like the Unity desktop of the netbook edition.

Unfortunately my Asus netbooks (Asus Eee PC1000, Asus Eee PC 1201N) are affected by the hibernate suspend bug that affects some machine.

Good news though as there is a simple fix to this bug, documented in the [Ubuntu 10.10 Maverick Meerkat release notes](https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes).  Here are the details of the fix.

<!-- more -->

**When the XHCI module is loaded for USB 3.0 operation the system cannot suspend.** 

Manually unloading XHCI will allow suspend to complete normally.  To avoid future suspend problems, the workaround is to add the following line to `/etc/pm/config.d/unload_module`

    SUSPEND_MODULES="xhci-hcd"

Ubuntu can then suspend normally - [see bug 522998](https://bugs.launchpad.net/bugs/522998 "Bug").

{% blockquote %}
Please note: this fix only seems to work when using the closed source nVidia drivers.  Using the open source nouveau drivers gives a black screen when awoke from suspend or hibernate.
{% endblockquote %}

**Implementing the fix - create a new configuration file**

Open at terminal window **Applications > Accessories > Terminal**

Enter the following command into the terminal window:

    gksudo gedit /etc/pm/config.d/unload_module

In the editor window that pops up, paste the following text and save the new file. 

    SUSPEND_MODULES="xhci-hcd"

Suspend and hibernate should now work as normal for some people.  Good luck.

Thank you. 
[@jr0cket](https://twitter.com/jr0cket)

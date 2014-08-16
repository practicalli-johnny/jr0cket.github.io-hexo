title: Making your Internet experience faster, more open
date: 2010-01-03 15:08:00
categories: dev-tools
tags: 
- dns
- google
---

{% img img-thumbnail http://techfreakz.com/wp-content/uploads/2010/05/google_dns.jpg %} 

If you find your browsing a little slow or find that some sites are blocked by your ISP, then you can try using the [Google Public DNS ](http://code.google.com/speed/public-dns/) as an alternative ([full set up details](http://code.google.com/speed/public-dns/docs/using.html)).  Here is the how and why of setting up your Internet connection via Google DNS on Ubuntu.

<!-- more -->

## Why is this a problem?  

Well for every page you access on the Internet the browser has to find that page based on the name you typed in the address bar or the name of link you clicked on.  The browser used a Domain Name Service (DNS), usually provided by your ISP.  DNS translates the address name into a number called the IP address (eg. 192.168.1.1) and once the IP address is known, the web page can be downloaded to your browser.   As this lookup happens each time you visit a different page, if your Internet Service Provider (ISP) has a poor DNS then your pages will be slower to display.  You can also be blocked from sites at the ISP's discretion (usually dependant on who the ISP is being sued by).

{% img img-code http://4.bp.blogspot.com/_yKz3swsAoNQ/S0C9-VB8GXI/AAAAAAAAABQ/8Sb_djXriKk/s1600-h/NetworkManager-GoogleDNS.png %} 

## Setting up your network to use Google DNS

Setting up Google DNS in Ubuntu is very easy.  Run the **Network Connections manager > System Preferences > Network Connections** , edit your current connection and select the IPv4 Settings tab.

Set the DNS servers to use the Google DNS first and second, with your existing ISP DNS server as a fall back.  Your entry should be:

    8.8.8.8, 8.8.4.4, your-existing-dns-server, your-isp-dns

> Note: All DNS server addresses should be separated by commas.  Keep a note of your existing server address as a backup just in case.

Apply the changes and close the network connection manager.  Restart your network connection using the network applet in the notification area of your panel.  Select disconnect for your current network connection, then select the connection name to connect back to the network.

You can test that you are now using the Google Public DNS by using the command nslookup or look at the contents of `/etc/resolv.conf`

Here is an example of the Google dns working when running the command `nslookup` on the BBC website.

    $ nslookup www.bbc.co.uk
    Server:        8.8.8.8
    Address:    8.8.8.8#53
    
    Non-authoritative answer:
    www.bbc.co.uk    canonical name = www.bbc.net.uk.
    Name:    www.bbc.net.uk
    Address: 212.58.253.68

Have fun on the Internet.

Thank you.
[@jr0cket](https://twitter.com/jr0cket)

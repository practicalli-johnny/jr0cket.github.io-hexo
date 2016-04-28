title: banterhack - BB-8 all the things
date: 2016-02-07 14:03:01
categories: events
tags:
- iot
- sphero
- bb-8
---

## Bluetooth address via Ubuntu settings
Discovered my BB8's blue-tooth number, `BB-7822` via the Ubuntu bluetooth manger.  There were a lot of bluetooth devices detected, but only one that started with BB.

I am assuming that this is the right address

## CLI tool

```
sudo hcitool lescan
```
This gives a list of all the bluetooth addresses found in range.  The address that is paired with the BB-* number is the right one (hopefully) 
`E1:C6:F5:69:78:22 BB-7822`

## Using node to discover the bluetooth address


Using `node ./node_modules/noble/examples/advertisement-discovery.js` to determine the MAC address was not of much use, but it did help find the device ID which ended up working. What my output ended up as was:

```
peripheral discovered (944f561f8cf441f3b5405ed48f5c63cf with address <unknown, unknown>, connectable true, RSSI -73:
    hello my local name is:
        BB-131D
    can I interest you in any of the following advertised services:
        []
    here is my manufacturer data:
        "3330"
    my TX power level is:
        -18
```


## Using web bluetooth via chrome


This is not supported in Chrome for Ubuntu.  Its not supposed to be that great on Mac.  It didnt work on my android phone.



## Using Linux & Python (may just be sphero & not BB8)

https://gist.github.com/ali1234/5e5758d9c591090291d6

Failed with lots of errors


## javascript official unoffical repo

Install

sudo apt-get install bluetooth bluez libbluetooth-dev libudev-dev


npm install noble sphero

A long list of bluetooth devices found, look for the BB- name

```
peripheral discovered (e1c6f5697822 with address <e1:c6:f5:69:78:22, random>, connectable true, RSSI -39:
	hello my local name is:
		BB-7822
	can I interest you in any of the following advertised services:
		["22bb746f2ba075542d6f726568705327"]
	here is my manufacturer data:
		"3330"
	my TX power level is:
		6
        ```


sudo /home/jr0cket/apps/nodejs/current/bin/node ./node_modules/noble/examples/advertisement-discovery.js


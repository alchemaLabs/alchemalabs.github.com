---
layout: post
title: "centOS 6 Truecrypt command line setup"
description: ""
category: linux
tags: [linux, truecrypt, centOS]
---
{% include JB/setup %}

I'm going to write this down so I can come back to it later. 

This is a fresh (minimal) install of centOS 6. You can find it here: [https://www.centos.org/](https://www.centos.org/)  

NB: the min install is really quite minimal. You will need to install most tools yourself. 

As I was saying... first we need wget

    yum install wget

Now to grab Truecrypt (TC from hereon)

    cd /tmp
    wget http://www.truecrypt.org/download/truecrypt-7.1a-linux-console-x86.tar.gz

Again, this is a min install of centOS so there are no GUI's involved and thusly no need for TC GUI. 

Open the tar, and execute installer

    tar zxvf truecrypt-7.1a-linux-console-x86.tar.gz 
    ./truecrypt-7.1a-setup-console-x86

Ay this point, I found I was missing some stuff. Hard to tell as I'm just looking through history...but you'll need fuse

	yum install libfuse
	yum install fuse-libs

Heh. Also had to install man

	yum install man


TC should be ready to go. Check `truecrypt -c` for info. 

Once you've initialized a volume and have mounted it via `truecrypt --mount` you need to remember to `umount /media/truecrypt1` before running `truecrypt -d` lest the lock will preven TC from unmounting the drive. 

Also, don't forget your passwords. 

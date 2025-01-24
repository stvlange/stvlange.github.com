---
layout: post
title:  "Rediscovering Radio (Part 1)"
date:   2025-01-23 20:45:00
categories: home radio ham
---

{% newthought 'Resurrecting my interest in ham radio' %} wasn't originally on my 2025 bucket list, but recently I've had an itch to get back into the hobby.<!--more-->  This time around, I decided to go about things a little differently.

{% marginfigure 'mf-id-1' 'assets/img/operator.png' %}Back when I stopped actively doing the hobby two and a half years ago I had a my radio setup in my basement with an antenna in the back of the yard that I would put up and take down as needed.

When I felt like using the radio, I would head outside and erect a telescoping fiberglass mast with an antenna that I built, head downstairs to listen and try to make some contacts, and then take the antenna down.

Setup of the antenna was always a pain but something I had to put up to avoid getting the HOA in my business and to avoid sparking spousal angst. And I was more than happy to take these extra steps, it was after all a hobby.
 
## Ham Radio Hiatus
Around that time we decided to have some landscaping done. Specifically we had eight evergreen trees planted, four on each side of the yard.

In talking to the landscapers I made it very clear where not to dig. I did not want my buried cable cut under any circumstances. Of course what happened? *They cut the cable.*

Aside from royally pissing me off, this effectively suspended my ham radio fun, and over time and various life events (some good, some bad), I just never got around to fixing the cable issue.

## Renewed Interest
{% marginfigure 'mf-id-2' 'assets/img/7300.jpg' 'ICOM 7300 HF Transceiver (<a href="https://www.icomamerica.com/lineup/products/IC-7300/">LINK)</a>' %}A few weeks ago I started to look into remote operation options for my ICOM-7300. Since July of this year I now have access to another property that just so happens isn't in an HOA and has large mature/tall trees.

A double win in the ham radio book. Nobody to say "no" to a permanent antenna of some kind, and plenty of tall trees that antenna wires can be strung up in.

The challenge was how to make the radio something that I could use remotely? ICOM sells some pricey remote operations software for windows that costs I believe $199.00 and has fairly mixed reviews.

## The "wfview" Open Source Solution
The alternative appears to be an open source project called "wfview"{% sidenote 'wfview' 'wfview | Open Source interface for Icom and Kenwood transceivers (<a href="https://wfview.org/">LINK</a>)'%}. Basically if you have a PC running wfview connected to the 7300 via USB you can control everything on the radio from that computer.

The exciting thing is that if you have another copy of wfview running from a remote location, you can cannot remotely to the wfview connected to the radio and *operate the radio exactly as if you were where the radio is located.*

If it works, it would allow me to permanently setup the radio at the remote house and use it whenever I wanted.

## Remote Server Setup
{% marginfigure 'mf-id-3' 'assets/img/pi-zero.jpg' 'My Raspberry Pi Zero (<a href="https://www.raspberrypi.com/products/raspberry-pi-zero/">LINK</a>)' %}To get up and running wfview can be setup on Windows, Mac OS or Linux. Since I didn't have any spare desktops that I could dedicate to being the remote wfview server, I decided to try getting it setup on an old Raspberry PI Zero (512mb RAM) that I had been using at one point as a DNS server.

This required me to re-image the system, and then re-setup the Adafruit Mini TFT display board that displays key system details such as IP address, CPU load, Memory, etc.

## Remote Access Setup
The Raspberry Pi Zero OS image comes with an version of VNC installed called "wayvnc" to make remote configuration of the Pi easier. I wanted to use this with a Linux VNC viewer on my Chrome OS Flex laptop called "Remmina".

Remmina had issues dealing with the certificates that the Pi Zero setup making the connection impossible. Plus I really didn't like the idea of opening VNC to the internet, so I decided to configure Remmina to tunnel VNC through SSH.

Once the SSH connection to the Pi Zero was established, I could then just connect to localhost since I was already connected to the Pi Zero.

It did require me to disable encryption in wayvnc and configure it to only listen on localhost, but that didn't matter since I would be coming over an authenticated SSH connection.

## Installing "wfview" from Source

I then needed to get wfview installed on Pi Zero. Unfortunately the version that is available on the operating system that the Pi Zero runs on (Debian Bookworm), is significantly behind the current wfview release.

The maintainers of wfview make a nice install script available for Debian that installs essential requirements, downloads the latest version of the wfview code, and starts a make compile process.

## Abort! Failure to Compile!
Trying to compile wfview on the Pi Zero is not a fast process. And the process kept aborting. From various forum messages I read the issue seemed to be due to lack of memory and swap space.

Digging into the Pi config I saw that I could change the amount of memory dedicated to the GPU, so I scaled that down from 64 to 16 by editing the "/boot/firmware/config.txt" file as root changing the "gpu_mem" value.

``` bash
    # Change GPU memory
    # default is set to 64, comment below to return to default
    gpu_mem=16
```

Next I saw that the Pi Zero by default only had a 512MB swap file. This I upped to 2048 by editing the "/etc/dphys-swapfile" file as root and changing the value to 2048.

``` bash
    # set size to absolute value, leaving empty (default) then uses computed value
    #   you most likely don't want this, unless you have an special disk situation
    #CONF_SWAPSIZE=512
    CONF_SWAPSIZE=2048
```

Next I updated the build script to change it from using "make -j2" to just "make" to try and help alleviate the CPU and memory availability

## Praying I can "make" It
With all these changes in place, I once again kicked off the build script and silently began to pray it would be enough.

Opening a second terminal window I fired up the "htop" command and sat watching the CPU being pegged at 100% and the memory jumping up and down getting dangerously close to the limit.

Thankfully, the make process was able to complete and "wfview" was successfully installed on the Pi Zero!
 
{% maincolumn 'assets/img/wfview.png' 'The "wfview" Interface seen via VNC over SSH on the Pi Zero' %}

## Next Steps
Next I need to configure wfview for the ICOM 7300 and confirm that I am able to control the 7300. Look for a "Part 2" on this in the near future.

---
layout: post
title: "Raspberry Pi Networking"
date: 2014-09-13 17:05:47 +1000
comments: true
categories: [Raspberry Pi]
---
I used to have troubles to set my Raspberry Pi to get connected to the existing network because I do not have keyboard and monitor to directly access it. The only thing I can do is plug off the sdcard and insert it into my laptop to get access to the OS.

But, my laptop is running on Windows, it does not recognize EXT partition. So, I can not easily modify the network configuration of the system. However, there is one partition on the sdcard that based on FAT32 which is can be easily read and write by Windows. This partition is boot partition. Now, I will show you how I can easily set up my network connection, whether to connect to LAN cable, existing WiFi, or even set my own access point!
<!-- more -->
Before we begin, you might need to check my [Raspberry Pi's specification](http://blog.eamca.com/blog/2014/bikinibottom/) beforehand.

The idea is a service will read a configuration file located in FAT32 partition during boot time. This will allow us to easily modify the configuration file before the Raspberry Pi is booted. Basically there 3 are steps to set this up.

1. Create service

   This is my simple service script located at `/etc/systemd/system/`. While booting, this service will execute a "reader" script.
   <script src="http://gist-it.eamca.com/github/spondbob/bikinibottom-mode/raw/master/bikinibottom-mode.service"></script>

2. Create the reader

   This reader file is to decide which network configuration going to be used. The reader reads a textfile which called MODE.txt file. Basically, MODE file contains the filename of the configuration files which will be executed by this reader.
   <script src="http://gist-it.eamca.com/github/spondbob/bikinibottom-mode/raw/master/bikinibottom-mode.sh"></script>
   Put it in a `your_filename.service` then enable it by `#systemctl enable your_filename`. And here is a minimal MODE file as a switch.
   <script src="http://gist-it.eamca.com/github/spondbob/bikinibottom-mode/raw/master/MODE.txt"></script>

3. Last but not least, the configurations

   Basically you can put anything what you like here, as long as the file name is included in MODE.txt to be executed when booting. Here I provide some of my network configuration.
   
   Static IP for LAN interface enables direct access to the pi.
   <script src="http://gist-it.eamca.com/github/spondbob/bikinibottom-mode/raw/master/scripts/eth0.sh"></script>
   
   Wireless configuration to connect to existing WiFi. Use `wpa_passphrase your_SSID your_password` to setup the profile.
   <script src="http://gist-it.eamca.com/github/spondbob/bikinibottom-mode/raw/master/scripts/wlan0.sh"></script>
   
   Setup access point with [ap_create](https://github.com/oblique/create_ap)
   <script src="http://gist-it.eamca.com/github/spondbob/bikinibottom-mode/raw/master/scripts/ap.sh"></script>

You might take a look [the complete project](https://github.com/spondbob/bikinibottom-mode/) on my Github. Feel free to drop a message if you got any questions.


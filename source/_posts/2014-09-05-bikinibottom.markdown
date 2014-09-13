---
layout: post
title: "bikinibottom"
date: 2014-09-05 17:30:57 +1000
comments: true
categories: [Raspberry Pi]
---
This page is specifically introduced my Raspberry Pi, bikinibottom, with its functionalities and features. Since at the time this page is written, bikinibottom is a Raspberry Pi runs Arch Linux ARM. Its mainly usage is as a standalone development server.
<!-- more -->
The attached hardware is listed as follows:

- Raspberry Pi Model B
- SanDisk Ultra SDHC Card 16GB
- Nano USB WiFi EDIMAX EW-7811Un
- Power adaptor 750mA, 1A, and 2A

The most usage applications are:

- Web servers: apache2, nginx
- Database servers: postgre, MongoDB
- Programming languages: PHP, python, ruby (on Rails)
- Multimedia: omxplayer, mopidy
- Torrent: rutorrent
- Other: rvm, git, tmuxinator

Partition table:
```
Disk /dev/mmcblk0: 14.9 GiB, 15931539456 bytes, 31116288 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x417ee54b

Device         Boot  Start      End  Sectors  Size Id Type
/dev/mmcblk0p1        2048   186367   184320   90M  c W95 FAT32 (LBA)
/dev/mmcblk0p2      186368 31116287 30929920 14.8G  5 Extended
/dev/mmcblk0p5      188416 31116287 30927872 14.8G 83 Linux
```

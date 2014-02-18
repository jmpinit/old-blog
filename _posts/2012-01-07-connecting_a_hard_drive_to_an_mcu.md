---
layout: post
title: "connecting_a_hard_drive_to_an_mcu"
description: ""
category: "old"
tags: []
---


[![](http://www.hackniac.com/blog/wp-content/uploads/2011/07/board-e1325956514326.jpg)](http://www.hackniac.com/blog/wp-content/uploads/2011/07/board-e1325956514326.jpg)

I've got a few dozen old hard drives just sitting in my junk pile, so over the summer I decided to attempt to interface them with an 8 bit microcontroller. The board above is what I came up with. It has an Atmega32 microprocessor wired up to two headers, which allows it to be plugged into an IDE hard drive.

<!--more-->

[![](http://www.hackniac.com/blog/wp-content/uploads/2011/07/setup-e1325955113943.jpg)](http://www.hackniac.com/blog/wp-content/uploads/2011/07/setup-e1325955113943.jpg)

Creating this board was easy enough, but the software was the challenging part. Finding good information on the IDE specification proved to be difficult, but eventually I found two sources that deal with combining IDE devices and microcontrollers specifically, [here](http://www.retroleum.co.uk/electronics-articles/an-8-bit-ide-interface/) and [here](http://www.pjrc.com/tech/8051/ide/wesley.html). It turned out that the information was hard to properly implement, and I spent a week working on the project with painfully little progress. Eventually I was able to read some data from a hard drive over the interface and spin up/down the drive, but that was it. I started to lose interest after it proved to be so difficult and unreliable, especially because it was supposed to be a small side project. Maybe in the future I'll take another shot at it and have less of a hard time, but for now the IDE experimentation is finished.

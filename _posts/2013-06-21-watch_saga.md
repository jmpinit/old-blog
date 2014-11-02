---
layout: post
title: "watch_saga"
description: ""
category: "old"
tags: []
---

Watch Saga
==========

![watch_hello](http://hackniac.com/images/posts/simulacrum/watch_hello.jpg)

School burnt me out so I took refuge in a small personal hackathon. Believe or not, this project went from conception to working hardware with "hello world" code inside of 4 hours. The only point to it was to build a small, portable platform for fun-to-write 8 bit code. I had all the parts in my junk bin, dead-bug soldered everything, made up the schematic as I went along, and worked like mad. It helped that I am extremely familiar with all of the parts that I used, and kept the design relatively simple (electrically unsafe).

Hardware
--------

![parts](http://hackniac.com/images/posts/simulacrum/parts.jpg)

Obviously it's gross and not super robust. I super-glued things together as I went along so there was no chance of repair. It just had to work the first time, and very luckily, it did. Surprisingly the formfactor feels pretty slim. I guess that's what you can buy with space left unused by a sane design.

__parts list__

* Atmega328P - the 8 bit, 8 MHz CPU with 32 KB of flash and 2 KB of SRAM
* RN-42 serial Bluetooth module - for loading firmware and games from a phone or PC
* 24LC256 serial EEPROM - for saving games and data like high scores
* 3.3v LiPo battery
* DC to DC boost converter - to manage the battery

Software
--------

![vm_run](http://hackniac.com/images/posts/simulacrum/vm_run.png)

I did a neat experiment with [the software](https://github.com/jmptable/simcrum) for the watch. I made it so that the C code for the firmware can be compiled for the AVR or for my PC. When it's compiled for my PC it gets run with simulated hardware devices that implement the APIs I defined. SDL is used to display the screen and manage threading. Because applications for the watch can be compiled and run on a PC the development time is much shorter than it would usually be. Normally I'd need to flash the compiled code to the device after every change, and that can take thirty seconds or more. And often hardware issues will obscure the software issues that I am testing for. Development is much more pleasant with the simulation framework, but it did require a lot more code to properly implement the hardware.

When I was working on this project I made [a thread on the TigSource forums](http://forums.tigsource.com/index.php?topic=34294.0) (an indie gaming forum).

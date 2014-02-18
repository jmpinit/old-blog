---
layout: post
title: "bootable_conways_game_of_life"
description: ""
category: "old"
tags: []
---


<iframe width="480" height="360" src="http://www.youtube.com/embed/eN8e23gVuS0?rel=0" frameborder="0"></iframe>

In late 2009 I was toying with x86 assembly. I worked out a way to take an existing x86 assembly program made for MS-DOS and run it in the 512 KB bootstrap space usually used to boot a larger operating system. My favorite experiment in this was getting my old laptop to boot into an assembly code version of the great cellular automaton Conway's Game of Life. My method relied upon the fact that the x86 architecture allows for a 512KB bootloader. I opened up the Conway's Game of Life executable using a hex editor and formatted it as if it were an operating system image, putting the game code in the space where the bootloader should have been and leaving the rest blank. Once I burned the image to a disc I was able to put it in a computer and load it as if it were a new operating system. The computer's BIOS would try to load the O.S. on my disc by running the bootloader, but instead the Conway's Game of Life executable would run.

It was a pretty fun project, and fired my imagination. After those experiments I came up with some very ambitious plans to write my own operating system in pure assembly, but eventually those plans were superseded by Greyport. Hopefully in college I will be able to return to that ambitious exercise and complete it.

---
layout: post
title: "<insert title here>"
description: ""
category: "old"
tags: []
---


I am writing the system with distinct modules, separating the communications system from the screen and sound interfaces for example. The bytecode interpreter will be mostly independent of the rest of the system. This means that I can write a couple and swap them in and out as I please. This is important because I don't have a concrete plan for the interpreter.

I considered doing a Forth machine to start, but that impulse was quickly killed when I remembered how much writing Forth code sucks (even it's proponents must admit that it's not great in the area of readability). Instead I am going to implement the DCPU16 from Notch's new game 0x10c. I've been following its development for some time and am continually amazed by its strong community, which has already developed numerous tools and applications for this made-up platform. The DCPU16 specification makes it fairly approachable, and it is widely available on the net with numerous open-source emulators available as examples. I love the idea of 0x10c and feel like it will go a long way towards nurturing a new generation of technological wizards. The ability for someone who loves that game to readily start playing with my own device is very exciting.

So! I will implement a DCPU16 emulator on Nibble to feed off of the hype, community, tools, and code currently flying out of 0x10c. And the theoretical children who will be playing 0x10c will have something familiar to play with, but that can cross the gap out into the real world.

---
layout: post
title: "ti_calculator_synthesizer_backpack"
description: ""
category: "old"
tags: []
---


[![](http://www.hackniac.com/blog/wp-content/uploads/2011/07/tynth_side-1024x768.jpg)](http://www.hackniac.com/blog/wp-content/uploads/2011/07/tynth_side.jpg)


## Math Class + Music?

For one of my personal hackathons a year or so ago I made this audio synthesizer backpack for my TI 84+. It contains an [Atmega168 emulating a SID](http://www.roboterclub-freiburg.de/atmega_sound/atmegaSID.html) (sound chip in the Commodore64) and audio amplification circuitry as well as a 9v battery for power. The backpack gets commands from the calculator through the link cable. It uses the [TI UART code](http://www.hackniac.com/posts/ti-83-uart.html) that I wrote so long ago to talk to the Atmega168 in its native tongue. From TI-BASIC I can do 45:Asm(prgmTX) and the number 45 will get sent to the Atmega168. Using some simple commands registers can be set in the emulated SID, and sounds result.

The case is an Altoids tin. I hot-glued pieces of metal to a spare calculator shell that I had so that I could bolt the case on. It worked pretty well and made the final result significantly more polished.

It was quite fun to mess around with. I wrote a complex TI BASIC program that served as a tracker (picture in gallery below). Composition was difficult, but it made simple music possible. Because it only took a day and it looked pretty snazzy it's one of the projects I am more proud of. It was a ton of fun to make.

[galleries broken for now, sorry]

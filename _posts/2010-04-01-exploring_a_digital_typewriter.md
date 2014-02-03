---
layout: post
title: "<insert title here>"
description: ""
category: "old"
tags: []
---


From my old hackniac blog.

![](http://hackniac.com/images/relic/typewriter.png)

Back in the time of the ancients typewriters were common. My mom happened to have an electric example of such a device that she held onto from that era. Months ago my little brother carried down from the attic and proclaimed it his. It didn't really work, but the sound and feel of typing on it were really nice. I "borrowed" it from my little brother for a quick disassembly and peek inside the inner workings. What I found was pretty neat.

<!--more-->

![](http://www.hackniac.com/images/relic/mainboard.jpg)

You can see the main control chip in the photo. It is designated as first line UA3010-A-ROM1, second line M50747-B93SP, and third line 113101. If anyone knows where I can find a datasheet for this chip it would be nice if you dropped me an email. There are two chips that appear to be drivers at the top of the control board. From the tracing I have done it seems they go to the motors in the carriage assembly and the paper roll motor. At the upper left of the board there is a black circle with a small hole in the center. This is a small speaker, apparently piezo-electric. It allows the typewriter to beep to signify things like reaching the end of the line, etc. To the left of the speaker you can see the connector for the keyboard ribbon.

I've soldered my own ribbon cable to the bottom of the connector so I can eavesdrop on the signals (not contributing to my brothers happiness I should add). There are 16 pins on the connector in two groups of 8. By using an Arduino as a logic analyser I was able to figure out that the first 8 pins are outgoing signals from the main microprocessor. The last 8 pins are incoming signals going to the microprocessor, each with a diode. When I figured that bit out I realized that it might be possible for me to wire up my own microcontroller and dupe the one inside the typewriter. I had to examine the keyboard for the typewriter to be sure.

![](http://www.hackniac.com/images/relic/keyboard_front.jpg)

![](http://www.hackniac.com/images/relic/keyboard_back.jpg)

The task of figuring out where all the traces went on the keyboard was an extremely arduous one. It took an entire day, but now I know what connections I have to spoof to emulate a key press on any key I want. The chart I ended up with also made me realize that the keyboard was set up like a matrix, with rows and columns (sort of). The most probable method for the typewriter microprocessor to figure out what key is currently pressed is for it to raise every outgoing pin in order, and check to see if any of the input pins are high. If that is what is actually happening then all I have to do is make my microcontroller wait for an outgoing pin to be raised high, and then really quickly raise the corresponding pin on the ingoing line so that I trick the typewriter into thinking a key has been pressed.

My final goal is to make a system contained entirely inside the typewriter that allows me to print out pictures rendered in ASCII characters from a computer or SD card. Should be awesome. Wish me luck :D

[edit: This project probably wins a personal "most failed attempts" award. I kept coming back to it with new approachs but never got it working. It finally became dirty and nasty enough that I gave up.]

---
layout: post
title: "exploring_a_w1525_word_processor"
description: ""
category: "old"
tags: []
---


From my old hackniac blog.

The other day my mom forced me to go to the local Habitat for Humanity store to look at some chairs she found for our kitchen. When I was there I unearthed a beautiful W1525 word processor, which I was able to purchase for $10 because the person in charge of the store thought it was junk. When I got it home I plugged it in and turned it on and was greeted by a wonderful clicking, purring, and buzzing sound. The machine has a green CRT display, 2 backup disk drives, and a single floppy disk drive, as well as an entire electric typewriter hidden under the panel on the top. The keyboard clicks into a special storage area on the back of the machine and plugs into it using a standard telephone jack.

At the base of the machine there is a panel that is held in place with simple phillips head screws. I took it off and found easy access to the motherboard of the machine. Some quick google searching showed me that it has 2 microprocessors, 2 rom chips, an sRAM chip, and several other miscellaneous chips. The microprocessor is an HD63B03XP, which has plenty of documentation available because of its use in the Atari ST intelligent keyboard. To me it seems that the whole system is ripe for hacking. There are several avenues that are open to get my own code to execute on the machine. The first two that are immediately apparent to me involve either direct programming of the microprocessor, or emulating the ROM chips. Either approach has difficulties, but I have confidence that I'll be able to work something out eventually.

[edit: I worked a lot on this project but did not succeed in my goals. I found and bought a book that had information on the CRT controller chip that was in the word processor. I tried to use that information to put things on the screen from another microcontroller. I also tried to inject graphics into the video RAM by emulating the RAM chips with an AVR. Eventually I broke the original PCB accidentally and had to give it up.]

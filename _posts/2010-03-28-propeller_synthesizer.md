---
layout: post
title: "propeller_synthesizer"
description: ""
category: "old"
tags: []
---


From my old hackniac blog.


![](http://hackniac.com/images/relic/synthesizer.png)

I love the idea of old computers. I haven't gotten my hands on any to play around with so I can't say I really love them directly. However, all that beeping, whirring, dithering, chirpy music, tape, and paper really fires my imagination. That's why I have been trying to emulate the things that I love about them, for what seems to have been ages.

This particular project is a continuation of a long line of creations stemming from an idea I had when I was in 8th grade. I tried to create a little computer built entirely within a keyboard. It didn’t take long before I had an LCD, Vinculum USB interface, and keyboard hooked up to my trusty Arduino. Sadly either the keyboard, my Arduino, or my code died in some way and the project never really got off of the ground.

I kept trying, building several versions of the project keeping the same theme. There were two music players, one simple note-taker with LCD, and one portable PropComp. They were all almost complete failures, but huge learning experiences.

All that fail has landed me here, at a project that I think may have finally (hopefully just temporarily) satiated my lust for the aesthetics of old computers.

I started it as a simple synthesizer based on the Parallax Propeller microcontroller. I found some code on the parallax forums that created a working MIDI synthesizer on the propeller. It was a simple matter to download it, modify it a bit, and put it onto my nice little demo board to play around with. After a short while I realized how unbelievably awesome it would be to put the whole setup into a keyboard, add some LED’s, throw in a battery, maybe attach an LCD (recession economics permitting), and patch in the accelerometer from a Wii nunchuck.

The result is this device, which is an IBM keyboard with LED strip, audio jack, volume control, power switch, and of course, Guitar Hero guitar strap. I carried it around for an entire day at school to show my friends, and although a bit heavy, I consider it stylish :D. [edit: oh god why]

The capabilities for this thing are virtually endless. Right now it acts as a simple midi synth with POV display capabilities (an odd but satisfying mashup), but I am in the process of writing code to allow it to act as a music player, text to speech device, and accelerometer-based music scratcher (8bit DJ!?).

[edit: this is one of my all-time favorite projects. When I graduated HS I gave it to my musician friend. She is in (maybe was in) this band [dogcar](https://soundcloud.com/dogcar)]

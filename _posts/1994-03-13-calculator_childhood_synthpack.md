---
layout: post
title: "calculator_childhood_synthpack"
description: ""
category: "old"
tags: []
---

All of these programs were designed to interact with my [calculator synthesizer backpack](http://www.hackniac.com/posts/ti_calculator_synthesizer_backpack.html). An AVR running a simulated SID chip (from the Commodore64) and glue interfacing code was plugged into the calculator's link port. The calculator could set registers in the SID emulation to make music.

#### SENDBYTE

__purpose__

Assembly program that sends the value of the ANS variable (bounded to 1 byte) over the link port using TI link protocol. Designed to be used from TIBASIC programs by setting Ans and then calling the program like so:

	3:Asm(prgmSENDBYTE)	// sends a byte of value 3

#### DISPCOL

Helper program for TRACKER that displays the level of a note graphically.

#### DISPHEX

Input a decimal number and this program outputs the hexadecimal equivalent. Useful for figuring out register values needed for the SID chip emulator.

![DISPHEX](../images/calculator_childhood/DISPHEX.gif)

#### PIANO

[Calculator synthesizer backpack](http://www.hackniac.com/posts/ti_calculator_synthesizer_backpack.html) test program. First it sets a bunch of registers in the emulated SID chip on the companion AVR to get pure tone output. Then it converts button presses into notes to play and sends the notes over to the SID emulation.

#### RFRESH

Helper program for TRACKER that refreshes information on the screen.

#### TEST

Sets registers on a SID emulation to enable sound output. When I was building the [synth backpack](http://www.hackniac.com/posts/ti_calculator_synthesizer_backpack.html) I'd run this program, send raw values using SENDBYTE, and then listen to the response.

#### TESTSYN

Interactive program for setting the registers of the SID emulation responsible for the type of sound output.

#### TRACKER

Music tracker/sequencer for composing music to play with the [synth backpack](http://www.hackniac.com/posts/ti_calculator_synthesizer_backpack.html).

![TRACKER](../images/calculator_childhood/TRACKER.gif)

__controls__

* left/right - move to the previous/next note
* up/down - increase/decrease the value of the note
* TODO - controls for fast up/down and playback
* 8 - move up one chunk
* 2 - move down one chunk

#### RAMSND

TODO
Axe program that plays through RAM as samples.

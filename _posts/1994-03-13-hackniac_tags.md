---
layout: post
title: "<insert title here>"
description: ""
category: "old"
tags: []
---

What
====

Below are all of the tags I used for this website in wordpress.

Why
===

It's sort of a simplistic summary of what I've put on here.

How
===

1. suck tags out of YAML headers in all post sources (markdown) and put into text file
2. open text file in vim
3. remove filenames with regex search/replace
4. select all lines
5. sort and remove duplicates

_like so:_

~~~
grep '^- ' > hackniac_tags.md
vim hackniac_tags.md
:%s/.* //g
VG:sort u
~~~

The Tags
========

* +
* 3310
* 9600
* Adventure
* Art
* Circuit
* Codeday
* Concept
* Dash
* Demo
* Device
* Exploration
* Failures
* Favorites
* Gallery
* Link
* Modification
* Relic
* Software
* Status
* Thought
* Utility
* Video
* ai
* ambition
* amp
* amplifier
* ancient
* arduino
* assembly
* attempt
* attiny
* attiny13
* attiny2313
* audio
* avr
* basic
* battery-powered
* binary
* bit
* bluetooth
* button
* calc
* calculator
* camera
* card
* cardboard
* challenge
* chip
* chiptune
* classroom
* clean
* code
* communication
* cut
* datasheets
* demo
* demoscene
* device
* dip
* disassemble
* disassembly
* diy
* draw
* dremel
* ds
* editor
* electronics
* ersat
* failure
* faire
* fancy
* fast
* friend
* fun
* gadget
* gameboy
* glue
* greyport
* hack
* hackers
* hacking
* hackniac
* hardware
* i2c
* image
* infrared
* instruments
* ir
* isp
* java
* keyboard
* lcd
* learning
* leds
* lego
* machine
* make
* maker
* mcu
* memory
* micro
* microcomputer
* microcontroller
* mod
* music
* network
* nintendo
* nokia
* nokia3310
* note
* nxt
* old
* organize
* organizer
* parallax
* pattern
* pda
* pen
* philosophy
* php
* picture
* plan
* plastic
* player
* playful
* portable
* processing
* programming
* prop
* propeller
* protoboard
* protocol
* prototype
* pwm
* random
* repurpose
* robot
* satellite
* school
* screen
* self-contained
* sensor
* serial
* small
* software
* solder
* sparkfun
* speaker
* status
* stepper
* synthesis
* tear-down
* text
* ti
* tibasic
* tile
* tilp
* timelapse
* tiny
* tool
* touch
* toy
* transistor
* uart
* update
* utility
* veroboard
* visual
* wav
* wavetable
* wheel
* wire
* wireless

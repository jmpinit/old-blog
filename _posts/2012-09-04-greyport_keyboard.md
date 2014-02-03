---
layout: post
title: "<insert title here>"
description: ""
category: "old"
tags: []
---


[![](http://www.hackniac.com/blog/wp-content/uploads/2012/09/keyboard_top-1024x566.jpg)](http://www.hackniac.com/blog/wp-content/uploads/2012/09/keyboard_top.jpg)

This is the best creation that came out of my [Greyport](http://www.greyportal.com/) project. It's a homebrew keyboard driven by an Atmega168. Output is ASCII over 9600 baud serial. The tactile switches are in a key matrix that is scanned continuously by the MCU. The master device that the keyboard is connected to can request things like the last keyboard state or the last key pressed.

<!--more-->

The keymapping is a little weird (modified QWERTY) but it is a very functional device begging to be included in a future project. Designing it taught me a lot about embedded electronics, although it wasn't really the best solution to the problem it solved in its parent project. I'm mostly proud of it because it looks pretty.

[Check out the keyboard's firmware on github](https://github.com/jmptable/greyport/tree/master/Code/Firmware/Keyboard/firmware_v3)

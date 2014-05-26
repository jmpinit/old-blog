---
layout: post
title: "calculator_childhood_emus"
description: ""
category: "subpost"
tags: []
---

<!-- TODO overview -->

# CHIPSIM2

![CHIPSIM2](http://hackniac.com/images/posts/calculator_childhood/CHIPSIM2_fib.gif)

My second attempt at a computer emulator written in TIBASIC. This version supported a simple output device (the number at the bottom left of the screen). Like all of my TIBASIC computer emulators, it was slow (the gif is sped up). In the GIF it is shown calculating the fibonacci sequence until it hits the max storage size of one of its registers (255).

# GRPHPUTE

![GRPHPUTE](http://hackniac.com/images/posts/calculator_childhood/GRPHPUTE.gif)

A bunch of time passed (a year?) and then I decided to take another pass at writing a computer emulator in TIBASIC. I used some tricks, like unrolling pixel reads, to substantially speed up the operation of the computer. I also wrote a suite of utilities to make writing programs for the computer less painful. The program in the GIF was the largest I ever wrote for the system, and was designed to print its result to the screen in hexadecimal (the font can be seen loaded in memory at the bottom of the second to last and last columns). Unfortunately the only save I had was when I found it again and decided to record a GIF was for an incomplete version of the program, so it only carries out a few cycles before crashing.

## FLASH

![FLASH](http://hackniac.com/images/posts/calculator_childhood/FLASH.gif)

An example of a utility function used by GRPHPUTE. Takes an assembled program represented as numbers in one of the list variables of the calculator and draws it onto the screen in binary form. Prior to writing it I had been using the drawing functions of the calculator to write programs pixel-by-pixel (bit-by-bit).

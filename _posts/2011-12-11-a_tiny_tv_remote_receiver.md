---
layout: post
title: "a_tiny_tv_remote_receiver"
description: ""
category: "old"
tags: []
---


I love working with the Attiny13 microcontroller because of how challenging using its sparse resources is, and I had a few of them laying around, so I decided I would use one as the brain of my IR receiver. In my parts bin I found an infrared receiver from an old VCR. The receiver keeps its output pin high except when it detects a infrared light at 38Khz, at which point it puts the output low. When a button on a TV remote is pressed an IR LED sends out a series of pulses of infrared light modulated at 38Khz that encode the specific button that was pressed, and those pulses are picked up by the IR receiver in the VCR and then are decoded by a controller and used to control the device.

It did not take long to get the IR receiver working properly - I tested it by hooking it up to a piezo buzzer so that pushing a button on a remote while aiming it at the receiver would generate a beepy noise. After that I had to figure out what the pulse code from the remote actually looked like, so I would be able to write code to respond to it. To accomplish that I connected the IR receiver to my Open Bench Logic Sniffer, which allowed me to record the messages sent by the remote. Luckily, it turned out that the remote I have uses an extremely simple and nonstandard (not RC-5) encoding system. Each message is 16 bits, with one long start pulse and then shorter pulse pairs indicating a 1 or a 0. Each pair starts with a short uniform pulse, and ends with a pulse that is either the same size or larger. I arbitrarily took the short one to be for 0 and the long one to be for 1. After recording the binary messages for a bunch of button presses I realized that I had guessed the right pattern. The thing that gave it away was that the buttons 0 through 9 on the remote were encoded with ascending binary numbers.

With knowledge of the encoding scheme I could start writing code for the Attiny13 to decode it. What I ended up with is an assembly program that waits for a message to be received using a pin-change interrupt, decodes the message, and then sends out the bytes of the decoded message over UART implemented in software. A pin is toggled every time a message is received, to show that the system is working properly. I won't go into gory detail about how the code is written because I will attach it to this post. Take a look if you are interested, it should be fairly easy to understand (assuming you have a solid grasp of assembly language programming).

After the code was written all that was left to do was to take my messy breadboard prototype and put it into a nice package:

[![](http://www.hackniac.com/blog/wp-content/uploads/2011/12/labelled_guts-1024x1024.jpg)](http://www.hackniac.com/blog/wp-content/uploads/2011/12/labelled_guts-e1323636442572.jpg)

An old and small mint tin serves well as the enclosure. I smashed a few holes in it to accommodate the USB cable, indicator LED, and infrared light receiver. An FTDI UART to USB converter chip breakout board that I had in one of my parts bins allows my computer to recognize the device as a serial COM port. With a little bit more programming, and a console-based Winamp control program called CLAMP, I soon had a Java program (developed in the Processing environment) to receive commands from a TV remote and control Winamp in response. Specifically, I can change both the Windows wave playback volume and the Winamp volume, skip forward a track, skip backward a track, pause, play and rate songs (using the number buttons on the remote). Because I wanted to use the setup from across the room I made the program display the current volume as a big white-on-black bar taking up the whole screen:

[![](http://www.hackniac.com/blog/wp-content/uploads/2011/12/use2-1024x768.jpg)](http://www.hackniac.com/blog/wp-content/uploads/2011/12/use2-e1323636418462.jpg)

When I want to use the receiver I just plug it into my computer, hang it by its cord over something nearby, and launch the control app on my computer. It works great. I can listen to music while lounging/working in bed and still have control over what is playing. The rating ability in particular is very helpful, because I have a huge collection of chiptunes from 8bc.org and need a way to sort out which tracks are good and which are bad. I can be working and suddenly hear a really good track play, pick up the remote, and hit "5" to mark the song as good to enjoy later.

As my first foray into infrared light communication, I could not be happier with this project.

[Attiny13 IR Receiver sourcecode](http://www.hackniac.com/blog/wp-content/uploads/2011/12/IR_Control.zip)

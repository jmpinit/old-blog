---
layout: post
title: "<insert title here>"
description: ""
category: "old"
tags: []
---

<iframe width="480" height="360" src="http://www.youtube.com/embed/p_Sm2s3hkeo?rel=0" frameborder="0"></iframe>

A long long time ago (middle of the school year) I was playing around with an Attiny13 and a Nokia3310 LCD. I wrote a bunch of demos (which I've documented [here](http://www.hackniac.com/posts/attiny13-and-nokia-3310-lcd.html)) but I didn't really turn the experiments into a real project. Yesterday I finally had the motivation to do something with the code that I had written. I have been working almost nonstop (except for sleep) on new Flash game of mine, and it started to turn into a grind. I was getting tired of Actionscript and its object-oriented softness. The challenge of making a little game system out of a Nokia 3310-compatible LCD (Sparkfun doesn't sell the 3310 anymore :< ) and an Attiny13 seemed like just the cure.

<!--more-->

I started out by wiring an Attiny13 to a Nokia LCD breakout board on a breadboard. Then in just a couple of minutes I had it alternately clearing the screen and making it black by using a C library that I wrote a while back for a different project that used a 3310 LCD (Greyport). Seeing those pixels change started my mind working and it wasn't very long before I had an idea for the game to write for the little system. I decided to do a version of one of those games where you fly a helicopter through a cave by controlling its height, because it seemed simple and fun, but mostly because I was pretty sure I would be limited to a single button with the Attiny13 already mostly tied up by the LCD. I was already using all 5 I/O pins on the Attiny13 (excluding PB5 on RESET) so I didn't actually know how I was going to even get one button working, but that's a problem I decided to solve later.

With a real goal in mind I looked back to the flashing LCD and realized that I would not be able to write the game in C. With the Attiny's 1K of programmable flash memory and 64 bytes of RAM I needed every bit of control over the hardware that I could get. I set out to write it in assembly code (which is about as close as you can get to the hardware without writing the program in pure binary). I should say that I am heavily biased toward assembly. Most programmers hate it, but if I had infinite time I would choose to use it always because it is so much more satisfying and challenging.

To start I dug out my old Attiny13 + 3310 assembly code demos and sliced out everything I didn't need. The only code I kept was LCD initialization stuff, and a software SPI routine that I wrote to get around the fact that Attiny13s have no hardware SPI. The major coding challenges were as follows:



	
  * Generating/storing the cave terrain

	
  * Drawing the cave terrain

	
  * Drawing the helicopter

	
  * Responding to button presses

	
  * Checking if the player crashed the heli

	
  * Displaying progress

	
  * Progressively speeding up gameplay to increase difficulty

	
  * Saving and displaying hiscores


I won't bore you with the details (there were many) because you can look at the code to see how I solved all those challenges in 1K of memory, but I will explain the three largest gotchas that I ran into:


## Creating Terrain


The first was generating the terrain. I set out with the vague idea that I would generate it on the fly, resulting in a potentially infinite game. However, when I started writing that code I hit what should have been the very obvious stumbling block that you need random numbers to generate a random terrain, and you don't have a random() function in assembly! After a little research I came to the conclusion that there was no suitable software-only solution for generating random numbers on AVR chips. I didn't want a hardware solution (KISS dammit) for getting random numbers, so I decided to forgo them completely and store a pre-generated terrain in memory.

After a little fiddling with Processing I had a program that generates a random terrain represented as a series of heights and hole sizes. I simply pasted those numbers  into the assembly code so that they would be stored in PROGMEM. The game reads them in sequence to display the terrain. Since I only had a little space left after writing all the logic the terrain is rather small. You can "beat" the game by running into the $FFs at the end of the random numbers (which is actually the start of the game code at the beginning of PROGMEM, because at that point an overflow has occurred). With a little optimization to reduce code size the terrain could be expanded to a pretty reasonable length. There are other tricks that I could have used to pack more random terrain into memory, but I was very limited with code size and I didn't want to spend forever on this project (I still need to make that Flash game after all) so I didn't bother. Feel free to modify the code and expand the game as long as you give me credit and show me what you did :)


## Displaying Progress


I just wanted to display a number! But all the high-level prototype methods I came up with used modulo. And modulo is fairly hard in assembly. It takes up too much code. So I decided that since this is hardcore project, the players are going to be hardcore. They can read hexadecimal no sweat! And numbers are very easy to display in hexadecimal instead of regular base-10 decimal. That's why the progress and score are shown to the player in hex. It was a small thing, but I think it represents the odd and frustratingly unexpected challenges that crop up when you work with tough constraints like this.


## The Button Input


So I said earlier in the post that I used up all the pins on the Attiny13 controlling the LCD. To play my helicopter game I needed at least one button. The solution to this problem turned out to be very simple. The LCD has a RESET pin that resets the LCD if brought low. My code toggled that pin before initialization as the datasheet for the LCD driver chip specifies. However, I found that it worked just fine if it was simply tied to V+. That gave me one free pin to use for the button. I added a pullup resistor and had a working button input. This brought the parts list for the project to one button, one 1K resistor, one Attiny13, and one Nokia 3310 LCD, which made me very happy because I love simplicity in hardware.


## Features


In the finished game you can pilot a helicopter through a cave by controlling its height with one button. Your progress is displayed in the upper left-hand corner of the screen in hexadecimal. When you crash your score (the distance you traveled) is shown to you, also in hex. If your score is higher than the high-score stored in EEPROM then the new high-score is stored in EEPROM.


## Code Finished


It took an afternoon and a morning but here's the breadboard version of the system running my little assembly helicopter game:


## [![](http://www.hackniac.com/blog/wp-content/uploads/2011/06/proto_heli1-e1308859371285.jpg)](http://www.hackniac.com/blog/wp-content/uploads/2011/06/proto_heli1.jpg)




## The Code


If you wish to build this project or see how I wrote the game then here is the code for the project:

[Tiny Asm Copter Code](http://www.hackniac.com/blog/wp-content/uploads/2011/06/TinyAsmCopter.zip)


## Finishing Touches


I grabbed a little bit of perf-board, a proper button, and an AAA battery holder from my junk pile and put the system into a nice little portable package that can be held in the hand.

[![](http://www.hackniac.com/blog/wp-content/uploads/2011/06/tinycopter_play1-1024x768.jpg)](http://www.hackniac.com/blog/wp-content/uploads/2011/06/tinycopter_play1.jpg)

I'm fairly proud of the soldering job. It was pretty hard to make it this compact using a DIP version of the Attiny13 and an LCD breakout board without anything shorting.

[![](http://www.hackniac.com/blog/wp-content/uploads/2011/06/tinycopter_back_batt2-e1308860309321.jpg)](http://www.hackniac.com/blog/wp-content/uploads/2011/06/tinycopter_back_batt2.jpg)

The high score/death screen:

[![](http://www.hackniac.com/blog/wp-content/uploads/2011/06/tinycopter_hiscore1-e1308860448206.jpg)](http://www.hackniac.com/blog/wp-content/uploads/2011/06/tinycopter_hiscore1-e1308860448206.jpg)

I'm putting together a little video demo of it which I'll post later. For now though I should probably go outside into the sun.

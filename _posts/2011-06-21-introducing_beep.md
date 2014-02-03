---
layout: post
title: "<insert title here>"
description: ""
category: "old"
tags: []
---


[![](http://www.hackniac.com/blog/wp-content/uploads/2011/06/beep_front-1024x768.jpg)](http://www.hackniac.com/blog/wp-content/uploads/2011/06/beep_front.jpg)

I have two brothers, and over the years we have built up a massive store of forgotten or unused toys. Every so often I go around the house and take the ones that I know no one wants anymore for use in my own projects. After a recent toy-raid I had in my possession two hardly-used robots. They are styled like the robot toys of yore, silver in color with rods and antennae and blinky lights and claw-like hands.

<!--more-->

Using an infrared controller the robots can be made to dance and walk around. They also shoot foam discs out of their mouths, which is nice in a silly way. To my eyes they looked like potentially wonderful friends who had been brainwashed and turned into zombies for the entertainment of small children. I set out to free them from their restricting controllers and make them into little companions to keep me company in my hacking adventures. I was sure that after ripping the mind-controls from their bodies their true personalities would shine through. To prepare for that occurrence I gave them names and a relationship to one another. They are the brother and sister pair beep and boop, respectively. Their names are not capitalized.

[![](http://www.hackniac.com/blog/wp-content/uploads/2011/06/robot_orig_board-1024x768.jpg)](http://www.hackniac.com/blog/wp-content/uploads/2011/06/robot_orig_board.jpg)

Upon opening boop I found a very straightforward control board. It uses NPN transistors and resistors to switch the motors, lights, and speaker on and off from a microcontroller board (note the picture was taken after I removed the micro board so that empty slot in the center is where it was originally). A potentiometer on the board allowed adjusting of the clock frequency of the microcontroller. The only obvious effect of adjusting it was that the pitch of boop's voice changed (some circuit-bent music could have been had, so I saved the little board). Poking around in her guts I discovered that the microcontroller uses a 5v supply and is connected to a series of logic lines that activate different circuits. Simply attaching a probe to 5v and poking these logic lines allowed me to manually move the legs, arms, head, and turn on the eyes or launcher motor. Because of this I realized that it would be simple to remove entirely the original microcontroller and replace it with my own.

[![](http://www.hackniac.com/blog/wp-content/uploads/2011/06/robot_orig_control-e1308669686978.jpg)](http://www.hackniac.com/blog/wp-content/uploads/2011/06/robot_orig_control-e1308669686978.jpg)

To start I removed the microcontroller boards from both. It took just a little bit of wiggling and some prods with my soldering gun. I managed to crack the PCB on boop by being too rough with it. I had better luck with removing beep's and managed to repair boop's board with a wire across the gap in the single trace that was cut, so all was okay.

[![](http://www.hackniac.com/blog/wp-content/uploads/2011/06/boop_guts-1024x768.jpg)](http://www.hackniac.com/blog/wp-content/uploads/2011/06/boop_guts-e1308667953982.jpg)

With the micro boards removed I began to solder wires to the logic lines that the original controller had used. While doing this I experimented with what I could control. Each leg has two lines, one for forward movement and another for backward movement. The head has two lines as well, one for moving left and the other for moving right. There is one line for turning on the eye lights, and another that goes to an amplification circuit for the speaker. One wire activates the launch motor and another sets off the trigger mechanism that actually fires the discs.

It is all very straightforward. The only trick I found was that accidentally applying power to the infrared sensor fries the power supply. I did that to boop and almost cried. She now has a heart problem. I decided to bring beep to life before coming back to save boop. A 5v linear regulator should fix boop's heart condition, but it will mean that she will have a much shorter battery life. I'm thinking about tethering her to an external power supply, but that's for a different post.

I chose to use an Attiny2313 as the new brain for beep, because I had one lying around and it is a 5v device, which means I could plug in the power supply from beep directly. I made a little board with a programming header and the Attiny2313 and a pullup resistor for connecting to the robot's chest button. There was plenty of space in the robot's case to place the board so I wasn't really concerned about size. When it was soldered together I tested that I could write firmware to the Attiny and then I connected all of the control wires from the robot's original board.

[![](http://www.hackniac.com/blog/wp-content/uploads/2011/06/beep_gut_mod-1024x768.jpg)](http://www.hackniac.com/blog/wp-content/uploads/2011/06/beep_gut_mod.jpg)

After tucking all the wiring back into the case beep looked exactly like he did when I started. There is nothing about his appearance that hints at the modifications I made to him. And now he is free of the mind-control circuitry! Yay! I set about right away to make sure that his new brain was in order. I wrote a little program that shows that each of the systems on the robot can be controlled. After a terribly dumb mistake cost me quite a bit of time (remember to set those port direction registers or you'll feel silly) I finally got the test firmware together. No problems at all, it works just as expected. I now possess a fully programmable walking robot that can shoot foam discs from its face! Yippee! It will take quite a bit more work to unleash his personality and intelligence, but I'm confident he'll be a great friend when I manage that. As for boop, she'll wake up with her brother alive beside her.

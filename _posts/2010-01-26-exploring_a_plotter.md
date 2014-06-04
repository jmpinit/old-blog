---
layout: post
title: "exploring_a_plotter"
description: ""
category: "old"
tags: []
---


From my old hackniac blog.

![](http://hackniac.com/images/posts/relic/plotter.png)

I saw a bunch of Youtube videos featuring plotters and printers and laser cutters that people had created which got me really excited about these XY drawing things that can cut/draw/print crazy shapes in a very evidently mechanical way that captures the imagination (at least mine), which inspired me to go hunting on Ebay. Before long I found a friendly Canadian willing to part with his XY plotter for around $50 total. I happily bought it and waited eagerly for my new possession to arrive. One day it came in the mail, and I have to say, just as a side note, this Canadian guy is excellent at packing things, it almost seemed artistic the way he crafted cardboard inside the package to keep everything in place.

<!--more-->

For a long time I kept the plotter just as it had come to me. It had some really cool features. I could draw with the arrow keys and make it do a test print. It made really beautiful noises as well, musical if you timed your button presses right. The idea of wrecking the original electronics seemed depressing to me, which was the main reason I left it alone for so long. After a while though I realized it wasn't much use to me if I couldn't print pictures from the computer, and so I resolved to hack it.

![](http://hackniac.com/images/posts/relic/circuit.jpg)

The original RS-232 interface was almost no use to me, although (and this is incredibly cool) the entire protocol the device uses is explained in the manual. I really wish modern electronics devices had their workings explained within their manuals, although nowadays there is no real need to program your own device drivers for every new peripheral you acquire for your computer. When I gave up on communicating with the plotter in the manner originally intended I decided to just strip it of its original electronics and start anew. When I opened it up I found a huge tray of components in a large PCB. A really notable thing that I discovered were two ancient microprocessors [edit: probably actually EPROMs] that had stickers covering a glass window. The things were so old that they could be erased by exposure to and ultraviolet light! I feel so smug with my fancy modern microcontrollers that can be programmed via SPI from my desktop computer in under five seconds. Besides the logic circuits there are two stepper motors in the rig, with a small actuator to raise and lower the pen and two infrared gate sensors so the controller can figure out when the stylus has reached its limits. My basic plan of action was to wire the three electromechanical parts and two sensors to a new controller so I could connect the plotter to my computer and make the plotter print whatever I wish.

![](http://hackniac.com/images/posts/relic/gate_sensor.jpg)

To replace the old plotter controller I chose my Make Controller that I received for Christmas a few years ago and that hasn't seen much use since. It has two stepper motor controllers built in that can handle up to one amp, making it ideal for controlling my plotter. Before I could try out controlling the plotter with the new controller I had to solder a new connector to the ribbon cable that connected the old controller to all the parts on the moving carriage. The ribbon cable is flat with flat contacts, which is why I couldn't just insert it into a breadboard. It took hours to solder some new ribbon cable because of how easy it was to melt the old cable. Soldering really is my least favorite part about electronics.

![](http://hackniac.com/images/posts/relic/make_controller.jpg)

With the soldering done I made a circuit on my breadboard to control the plotter with my Make Controller. After that was done it really only took a few minutes to get a Processing sketch together to play with the stepper motors. Sadly I can only control one motor at a time right now because one of the motor controllers is burned out. I am replacing it with an EasyDriver that I got from Sparkfun, but it will take time to write code for controlling it, as I will have to write some new firmware for the controller. When the new controller is in I will have full control of both axes and will then be able to interface the gate sensors to complete the setup. With the gate sensors connected and with the right code I'll be able to make the plotter initialize to a home position on start-up and make adjustments as it runs to keep it accurate, because I know where the sensors are and the controller can tell when the carriage gets to one of the sensors, telling me where in absolute space the pen carriage is.

When everything is hooked up and I write the software on the PC side I will finally be able to start drawing things with my refurbished plotter. I might take one of several routes from there for the actual drawing mechanism. I could use a pen like it was originally designed to use, or I could use a laser powerful enough to burn/etch/cut, or even some kind of spray-paint system. A fun thing to do would be to use the plotter to print designs on shirts and then sell them for some money. Conceivably I could make a three color paint system with some piping and pumps so full color images could be printed, but I have a feeling that is better said than done. Lot's more experimentation to do, but I have faith the result is going to be quite spectacular.

[edit: it wasn't spectacular. Nothing more was done with this.]

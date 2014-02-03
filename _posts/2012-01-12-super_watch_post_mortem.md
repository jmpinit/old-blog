---
layout: post
title: "<insert title here>"
description: ""
category: "old"
tags: []
---


[![](http://www.hackniac.com/blog/wp-content/uploads/2012/01/watch_back-1024x980.jpg)](http://www.hackniac.com/blog/wp-content/uploads/2012/01/watch_back.jpg)

I wanted to make myself a watch a few months ago, so I rifled through all the parts I had on hand and picked out my favorites. Then I spent a day enjoying the painstaking process of making this mess.

<!--more-->

It's an infrared temperature sensor (left side above middle), infrared TV remote receiver (on top left), infrared LED (legged thing on right), and surface-mount Atmega168 attached to a Nokia 3310 B&W; graphical LCD. I also had an EEPROM chip and accelerometer picked out for it, as well as a lithium ion battery to power it all, but I never got far enough in the project to add them in. The wire hoops on the lower left were designed as a minimalistic programming interface.

[![](http://www.hackniac.com/blog/wp-content/uploads/2012/01/processor_connect2_lowres.jpg)](http://www.hackniac.com/blog/wp-content/uploads/2012/01/processor_connect2_lowres.jpg)

As its biggest plus, it shows how finely I can solder. The magnet wire (just normal solid wire with thin coating) was soldered to the surface-mount Atmega168 by hand with no magnification. Maybe I am a decent surgeon in another life...

The wiring was only completed to the programming interface and the LCD. Once I was able to power it up and get code into it I saw that the LCD connection was flaky. It required pressure in a very particular spot and in a very particular direction for anything to show up on the screen. I tried using glue to secure it and fix that problem, but it only made everything worse. Eventually my frustration with the LCD killed the project.

It was an interesting attempt, but I think it was doomed from the start because I focused purely on the fun of it and held nothing back to spend on making a solid structure. I jumped right into building it without any kind of design stage beforehand, just a few sketches to get a sense of what pins were where. Many of my best projects have progressed like that (notably [Tiny Miasmata](http://www.hackniac.com/posts/tiny-miasmata.html)), but it requires a very fine balance to pull of correctly. Fluidity is hugely useful in creative pursuits, because it links the mind more closely to the work, but it's also dangerous in the engineering world. Complex systems are often not forgiving. But this is what I like to do.

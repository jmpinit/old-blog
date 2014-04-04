---
layout: post
title: "microfluidic display"
description: ""
category: hardware
tags: []
---

# Microfluidic Screen

![the design](http://hackniac.com/images/microfluidic_screen/microfluid_screen.png)

## Background

One of my classes is [Nanomaker](http://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-s079-nanomaker-spring-2013/), which is all about learning how to make tiny things as cheaply and easily as possible. Every week in lab create something that either exploits or is nanotechnology, like spectroscopes, holograms, [inorganic EL devices](http://owen-t.me/hardware/2014/03/01/diy-el.html), or microfluidic devices.

Lately we've been focusing on microfluidics, which is an area that especially excites me. Microfluidics takes the manufacturing ideas developed so extensively in microelectronics and applies them to manipulation of fluids. Not only can you shrink anything that involves "plumbing" (as long as the application still works with less fluid, like most tests in labs), but you can take advantage of the weird physics that fluids exhibit in small quantities and spaces. Normally weak effects like surface tension and Van der Waals forces start to reign supreme when dealing with microliters of fluids.

Given the chance to build my own microfluidics device because of the Nanomaker class, I wanted to do something more interesting than shrink an existing lab test (what was encouraged). Most academic applications of microfluidics seem to focus on improving lab work (lab-on-a-chip), because that is what the researchers are most familiar with. It's true that the impact of microfluidics applied in labs has the potential to be huge (both in efficiency gain and money), but I think that the technology will eventually have a much bigger impact when it is used in machines that will enrich the lives of ordinary people.

# Results

This is the first iteration. I haven't set up the computer controlled valves necessary to actually display an image on my design. And there are manufacturing problems to address, explained below.

![before test](http://hackniac.com/images/microfluidic_screen/held_sm.jpg)

![left part of slide](http://hackniac.com/images/microfluidic_screen/slide_left.jpg)

![right part of slide](http://hackniac.com/images/microfluidic_screen/slide_right.jpg)

![poor image](http://hackniac.com/images/microfluidic_screen/bright_light.jpg)

## Problems

* Channel walls lifted off of glass and allowed fluid to leak.
* Channels collapsed. A single collapse anywhere in the screen channel completely ruins the device.

## Solutions

* More space between the channels so they are less likely to lift off of the substrate and leak fluid.
* Use the input ports with computer controlled fluid supplies instead of a syringe operated by hand. Should greatly reduce stress on the channels. And then I'll actually be able to display images!
* Larger hole or more holes at output, so pressure doesn't build.
* Increase the height of the channels. Currently about 20 micrometers, but should probably be doubled to eliminate channel collapse. Difficult to accomplish with wax printer method (explained below).
* Place air drainage channels in the area not used by the design, so that air trapped under the PDMS can escape and not reduce bond strength.
* Wait longer for curing and bonding to happen.

## How it is Designed

What I made is a first stab at a microfluidic display. The concept behind how it works is straight-forward. On the left are the ports for getting liquid into and out of the display. On the right is the display array itself, which is simply one long, continuous channel snaked in a particular way.

In order to display an image a little extra machinery is needed besides the microfluidic device itself. Two reservoirs of colored fluid supply the display. These fluids might be colored black and white, for example. They feed the fluid, under slight pressure, to computer controlled valves. The valves allow either one fluid or the other into the display itself, via the two input ports. Each fluid stays separate for a short distance in their own channels but soon combine into one flow where their channels meet. Thanks to the peculiar nature of fluids on the microscale the colors will stay as separate "plugs" in the channel. This is mostly due to a lack of turbulence in the flow (edge effects in the channel help achieve the lack of turbulence, but I won't get into that here). Given enough time the fluids would mix thanks to diffusion, but the process is very slow (hours) and the fluids don't stay in the display for long.

To actually put an image on the display, a computer turns the valves on and off in an order that corresponds to the pixels of the desired image. The plugs of colored fluid move through the display channel until they reach the output port. At that point the different colored plugs are all in just the right places for the image to be visible.

## The Weird Squiggled Channel

The reasoning behind the pattern of the display channel is really the only clever aspect of the design. It's a [Hilbert curve](http://en.wikipedia.org/wiki/Hilbert_curve), which is known as a space-filling curve (also a fractal). A one dimensional data set mapped into two dimensional space via a Hilbert curve maintains locality. Simply put in the context of my display, it's harder for little errors in the size of the fluid to add up and wreck the image that is produced. To make this clear, imagine that instead of the Hilbert curved channel the design simply used a channel that goes in a straight line from left to right, and then turns and loops back right to left, over and over. You can imagine that if a whole stream of pixels was pushed down that line, an error of one pixel would shift every line before it and completely ruin the image. In a channel with a Hilbert curve, an error like that would still mess up the image, but it would be harder to notice because the pixels are still very close to where they need to be.

# Manufacturing Process

![the template](http://hackniac.com/images/microfluidic_screen/transparency.jpg)

Happily, it is actually pretty easy to create microfluidics devices like this one.

## Materials

* [Wax printer](http://en.wikipedia.org/wiki/Solid_ink)
* overhead transparency (sheet of clear, flexible plastic the size of a piece of paper that can be fed through a printer)
* glass microscope slide (other substrates might work, but it's easiest to bond PDMS to glass or other PDMS)
* petri dish or similar container (ideally plastic and disposable, because you might need to break it)
* latex gloves (finger oils are bad)
* Scotch tape
* [PDMS](http://www.ellsworth.com/dow-corning-sylgard-184-silicone-encapsulant-0-5kg-kit-clear/)
* source of [coronal discharge](http://en.wikipedia.org/wiki/Corona_discharge) (we used a special tool, but the flyback transformer from a TV would work)

## Setup

* Mix the PDMS and leave it in a vacuum chamber for a while (if possible) to remove all of the bubbles.
* Clean the substrate (glass slide) extremely well. Ideally with strong solvents. Any contaminant will harm bonding to PDMS.

## Procedure

0. Put on gloves. Your skin oils will ruin everything. Don't touch the gloves' fingers while you are putting them on.
1. Print design onto transparency using wax printer.
2. Carefully heat transparency (hot plate at 100 degrees F or really carefully in toaster oven) to reflow the wax ink. Should only take 3 to 4 minutes.
3. Put transparency into the bottom of your petri dish or other container. Pour the PDMS on top, being very careful not to introduce air bubbles (they'll ruin your design).
4. Let the PDMS cure. Heating it up a bit (100 degrees F) will speed this up.
5. Carefully remove PDMS from container. Might require breaking the container. Be really careful not to tear the PDMS. Use as little force as possible. From here on out be extremely careful not to contaminate the bottom of the PDMS where your design is.
6. Peel off the transparency. Do it slowly and with a small angle between the PDMS and transparency so that the ink stays on the transparency.
7. Cut out your design (ideally the same size as the microscope slide / substrate). Scissors work fine. Knives are hard because they stick in the PDMS.
8. Pierce holes through the PDMS into the ports. Best to use the piping that will eventually be in them to get the sizing right.
9. Stick clean Scotch tape to the design-side of the PDMS and then remove. This should get rid of surface contaminants like dust and the remaining wax ink. If some ink is left on the design use a solvent like isopropyl alcohol to clean the channels. Don't get any solvent outside the channels or it will be hard to bond the PDMS to the substrate.
8. Blast the design-side of the PDMS and the top of the substrate with coronal discharge for about a minute. It's ok and even good to have surface surface arcs. This tears bonds all over the surfaces (particularly removing OH groups) so when they are stuck together molecular bonding can occur.
9. Carefully stick the PDMS to the substrate (with design against substrate). Don't mess up, because separating the PDMS from the glass after they touch is hard and likely to reduce the strength of the bond.
10. Wait a while for molecular bonding to occur. Ideally heat the whole thing at 100 degrees F for a while (30 minutes or more).
11. It's done!

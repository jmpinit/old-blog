---
layout: post
title: "solar gates"
description: ""
category: concept
tags: []
---

# /// SOLAR GATEs ///

## Inspired by:

* [BEAM robotics](http://www.m27.com/projects/beam/) - solar powered robots with minimal part count, analog design, and elegant structure.
* [Flip dot displays](http://www.youtube.com/watch?feature=player_detailpage&v=O9zQgDzH188#t=134) ([explanation]((http://www.youtube.com/watch?feature=player_detailpage&v=O9zQgDzH188#t=134))

## Description

Solar gates are small robots about the size of sugar cubes which together take sunlight and turn it into computation.  

Each one gets its energy from the sun using a solar panel, and stores it away in a capacitor to be spent in bursts using a circuit called a solar engine (from BEAM). On top of each, next to the solar panel, is a light collector, which is a lens that funnels the light of the sun into a strand of fiber optic cable. The cable turns the light 90 degrees, so that unimpeded it will shoot out the front of the robot in a tight beam. However, an electrically controlled shutter can block this light (designed like a flip dot). The shutter also acts as a flag, painted white on one side to represent "open" and black on the other to represent "closed". This makes the state of every solar gate obvious at a glance. Lastly, on the back of each robot is either one or two light sensors, mounted parallel to the surface that the robot sits on.  

Every time a solar gate has enough energy stored up in its capacitor, it carries out a Boolean logic function. It reads its sensors, and treats a light level above a certain threshold as "true" and below as a "false". Then it either opens or closes its shutter according to its particular function. The choice of which function a particular solar gate will carry out is up to the person playing with them, because they are programmable and can take on any possible 2 input Boolean function.  

By arranging solar gates on a sunlit surface digital logic circuits can be formed, because the light beam from one solar gate can activate the input of another. The gates evaluate randomly, whenever they collect enough power to operate, so the resulting circuit exhibits probabilistic behavior instead of the usual synchronous behavior. But any function can still be built using the solar gates, and it will be slowly executed using the power of the sun.  

## Features

* Extremely cheap, because the circuitry is so minimal. Each gate could easily cost less than a dollar.
* Easy to manufacture in great quantities. The logic and mechanical structure can both be had via a PCB, and the rest can be formed with one or two parts cut out of thin plastic or plywood.
* Aesthetically pleasing, philosophically and visually. Philosophically, using the gates is very intuitive, because they are extremely simple and the important aspects of their operation are obvious. Also, their operation under the power of the sun takes them partially out of the realm of "electronics" and into the realm of objects that are alive, because they are self-sufficient. A circuit could remain on a desk all day, calculating according to its design, go to sleep at night, and then start again in the morning with no need for human intervention. Conceivably a solar gate circuit could keep operating on its own for many years, until the mechanical parts start failing. Visually, each gate can be made into a beautiful crafted object. And a full circuit would be calming to watch and listen to, as the shutters snap back and forth, and thin beams of sunlight cut between the gates.
* Intuitively teaches digital logic.

## Improvements

### Synchronous Circuits

* Manually - cover all of the gates and lift the covers in the correct order by hand to allow the gate to fire. Or keep the circuit in darkness and fire the gates using a mirror or flashlight.
* Light flashes - have a central "clock tower" that rests in the center of the circuit and flashes at regular intervals using solar or battery power. An extra light sensor on ever gate detects the flash and fires the gate. Problems crop up when the gates charge at different rates and some of them don't successfully fire. Possible to mark this visually using an extra flag that is raised when the gate fires and falls when it is charged. Then the user could fix bugged gates manually.

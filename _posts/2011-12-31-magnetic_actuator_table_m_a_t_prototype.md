---
layout: post
title: "magnetic_actuator_table_m_a_t_prototype"
description: ""
category: "old"
tags: []
---


[![](http://www.hackniac.com/blog/wp-content/uploads/2011/12/mat_circuit.jpg)](http://www.hackniac.com/blog/wp-content/uploads/2011/12/mat_circuit.jpg)

A rectangular slab rests on a table with a camera pointed at it from overhead. Two wires snake out of it, one plugging into the wall and the other into a computer. I walk up to the slab with my hand full of steel ball-bearings, and dump them on the middle of its surface. Instantly they disperse, space themselves out equally, and conform precisely to the edges of the slab. Bringing over an unsorted box of my beloved Legos, I dump those on the surface of the slab too. With the press of a key on the computer's keyboard and the bearings launch into motion again. They swarm the messy pile of Legos, pushing them intelligently into clumps. Groups of bearings fly around with carefully choreographed motion, moving the clumps until I'm left with a few piles of sorted plastic parts. As quickly as the process started it ends, and the bearings again are at the edge of the slab, ready to handle another job.

<!--more-->

The M.A.T. is a project that I worked on for the final project in my AP physics class last year.  It was after the AP exam and we had just finished learning the basics of electromagnetic theory (one particular hell that I want to soon return to). I had obtained a love of magnets. Immense complexity in the fields contrasting with the ability to calculate them accurately using a small set of elegant equations piqued my tendency to obsess, and I was off. Within a short amount of time I had this concept together.

A Magnetic Actuator Table moves stuff with magnets. The idea is to embed a grid of electromagnets under a surface and control them intelligently using a computer. By placing a ferrous object on top and turning on the magnets in precise patterns an arbitrary force can be applied to the object. A camera looking down at the surface provides feedback to the computer so that it can precisely position objects using the magnets.

[![](http://www.hackniac.com/blog/wp-content/uploads/2011/12/mat_game.jpg)](http://www.hackniac.com/blog/wp-content/uploads/2011/12/mat_game.jpg)

I didn't have the money to build a prototype M.A.T. for my physics project. Instead I had to satisfy myself with making a simulation of it written in Java. It serves as a test bed for control algorithms and should allow the math needed to be worked out without actually having real hardware to test it on. Sometime in the future I hope to return to the project and actually build a working hardware prototype.

The general design for the hardware uses some half-bridge motor drivers, a pulse width modulation controller, and a fast microcontroller. The motor drivers would drive the magnets (motors are really just electromagnets with extra hardware, so this should work well) and the PWM controller connected to those drivers would allow the strength of each magnet to be easily modulated by the microcontroller. States for the magnets would be pushed over USB from the computer, where all of the real processing would take place. Computer vision algorithms could be used to track the objects being manipulated, and the other math would be fairly straightforward. Although solving the electromagnetic equations can be extremely computationally expensive I don't think they represent a major challenge to make a M.A.T. work because a good approximation would be sufficient.

[![](http://www.hackniac.com/blog/wp-content/uploads/2011/12/mat_use.jpg)](http://www.hackniac.com/blog/wp-content/uploads/2011/12/mat_use.jpg)

I want to return to this project in the future and make a working prototype. Hopefully I'll have enough resources to do it properly by then.

Here's the simulator code:

[Source Code](http://www.hackniac.com/blog/wp-content/uploads/2011/07/Mat_Simulator.zip)

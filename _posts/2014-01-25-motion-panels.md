---
layout: post
title: "motion panels"
description: ""
category: "concept"
tags: []
---

<!-- TODO JS simulation of resistor example -->

# The Idea

An affordable table that can rearrange the items placed on top of it in position and rotation under computer control. Useful for reconfigurable assembly-line processes like object sorting, lab sample processing, and electronics assembly or disassembly.

# Inspiration

* [3DOF Ultrasonic Levitation](http://96ochiai.ws/3DOFacoustic)
* [Leidenfrost Maze](http://youtube.com/watch?v=vPZ7sx3EwUY)
* [Bristlebots](http://www.youtube.com/watch?v=rUSTXUis_ys)
* [Vibratory Conveyor](http://www.youtube.com/watch?v=0eDWGMLf8dQ)

## Construction

__Physical Layout:__

1. bottom <- thin PCB  
2. middle <- piezoelectric transducer  
3. top <- textured plastic  

The transducer + logic on PCB allows the panel to vibrate, and to very roughly measure the weight of what is on top of it (_how:_ set up a vibration and then immediately switch to measuring the amplitude of the response).  The __textured plastic__ turns the vibration into forward motion of objects on the panel, because the texture is a sawtooth (as in the Leidenfrost Maze project).  

### Texture Types

* Straight - moves objects in one direction.
* Randomized - scatters items on top of them, so that groups of objects can be separated.

### Producing the Textures

* Press a mold into hot plastic
* Etch metal (copper & ferric chloride for easy prototyping?)

## Example Use: Sorting Resistors

A coffee-table sized table covered in a grid of squares (each about 1 inch on a side). A user would have a bucket containing many of each type of the panels described above.  Following a design tailored to their use case, they would plug the panels into the table. as each gets plugged in, it makes a connection to control electronics in the table, as well as a computer.  

With the panels arranged for the task the user could start making use of the table. Here the example is the sorting of through-hole resistors.

The user takes a handful of resistors and then places them onto the rectangle of input squares placed as part of the design. These vibrate and scatter the resistors outward. As each resistor leaves the input squares it enters a "conveyor" - a line of cells that vibrate to move the resistor down a particular path.

As the resistors are spread onto the conveyor they will sometimes spread out insufficiently. Because there is weight feedback from the squares it is possible to send clumped resistors back onto the input panels in order to break them up. At the output of the first conveyor each square only contains a single resistor at a time.

At the end of the conveyor is a row of special cells. Each one of these cells is a box with the top face occupied by a downward-facing camera. The conveyor pushes resistors into these cells so that their resistance can be identified from their color band code. In other applications there could be all manners of such special sensor cells to collect information during processing.

After the resistor's value is determined it is sent to the edge of the table and allowed to fall off the side. It falls into a bin corresponding to its value. When the table is done doing its job all of the resistors will be sorted into these bins.

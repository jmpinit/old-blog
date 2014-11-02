---
layout: post
title: "motion panels"
description: ""
category: "concept"
tags: []
---

# The Idea

An affordable table that can rearrange the items placed on top of it.  

# Inspiration

* [3DOF Ultrasonic Levitation](http://96ochiai.ws/3DOFacoustic)
* [Leidenfrost Maze](http://youtube.com/watch?v=vPZ7sx3EwUY)
* [Bristlebots](http://www.youtube.com/watch?v=rUSTXUis_ys)
* [Vibratory Conveyor](http://www.youtube.com/watch?v=0eDWGMLf8dQ)

Each of their arrays has 285 transmitters. Each transmitter costs $5. So with 4 arrays that's about $5700 just for the ultrasonic transmitters.  Clearly cost is prohibitive for reproducing this project, so I started thinking about cheaper ways to accomplish similar goals.  

## Motion Panel

1. bottom <- thin PCB  
2. middle <- piezoelectric transducer  
3. top <- textured plastic  

The __transducer__ + logic on PCB allows the panel to vibrate, and to very roughly measure the weight of what is on top of it (_how:_ set up a vibration and then immediately switch to measuring the amplitude of the response).  The __textured plastic__ turns the vibration into forward motion of objects on the panel, because the texture is a sawtooth (as in the Leidenfrost Maze project).  

### Texture Types

* Straight - moves objects in one direction.
* Randomized - scatters items on top of them, so that groups of objects can be separated.

## Motion Table

A coffee-table sized table covered in a grid of squares (each about 1 inch on a side). A user would have a bucket containing many of each type of the panels described above.  Following a design tailored to their use case, they would plug the panels into the table, l. as each gets plugged in, it makes a connection to control electronics in the table, as well as a computer.  

once the design is done, it can be put to use  

for example  

i have big handfuls of unsorted resistors  

i throw a handful onto a particular section of the table covered in squares of the randomized texture. these vibrate and scatter the resistors to the periphery. as each resistor crosses the edge, it enters a "conveyor" made from the straight sawtooth texture. the computer is getting constant feedback from the squares, so it knows when it has just a single resistor on a given panel. that's how it is able to jostle the resistors around intelligently (a stochastic process failing and retrying repeatedly) until just one resistor is on each square  

the computer then sends each individual resistor to an open square on one edge of the table.  

this is a special square  

it has a super cheap, low-res cell phone camera with a macro lens held above its surface by standoffs at the edges. a little light next to the camera illuminates the square. so when a resistor enters the square, a picture can be taken of it and sent back to the control computer. the control computer reads the resistor's color code and determines where it needs to go.  

then the resistor is sent out across the table to another edge where there are waiting bins  

it falls into its correct bin  

in this way, all of the resistors are eventually sorted  

now, that's a use case that i am interested in especially. but there are so many other things you could do with this idea  

larger objects could be moved by activating multiple panels at once  

possibly, with the right arrangement of panels, you could move objects like books or pencils or etc. in arbitrary patterns  

imagine a table that can intelligently rearrange the items on it  

if you're sold on that  

then here's the best part  

it's not prohibitively expensive. each panel costs less than 50 cents.  

the transducers can be sourced for a few cents at volume. same deal for the plastic  

the PCB only has a few components on it (really just the connector back to the table and maybe an amplifier)  

my trick for the plastic texturing is to heat the plastic and press the pattern into it from a metal form  

the metal form can be manufactured using etching. it's an identical process to normal home PCB manufacturing  

except that you repeat it several times to get a 3D structure  

for a prototype, we could even just use copper clad board and ferric chloride, entirely the same materials and process as PCB manufacturing  

regular ABS sheets should work to make the panels, which can be cheaply sourced  

so the first proof of concept stuff is about physics and routing  

i imagine a simulation program made using a physics library like Box2D. it would be a 2D, top-down sim of an arbitrary table design  

that way we could see what problems there are in routing objects on a surface like that. and test potential solutions  

and try writing algorithms to generate designs for specific applications  

i think a basic sim like this would be an afternoon project  

first physical prototype would be made by finding a surface with a sawtooth texture, cutting a square out of it, epoxying it to a piezo transducer, applying various signals to it, and seeing how objects behave when placed on top  

then video explaining the concept, showing this first example panel, and showing applications modelled in the simulation  

then that goes on IndieGoGo, and money comes in for making a full scale prototype

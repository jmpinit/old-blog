---
layout: post
title: "panda with a gun"
description: ""
category: software
tags: []
---

<!-- TODO link to post about VLLA color calibration -->

Context
=======

A few years ago my friend Ben made [a very bright 60x32 pixel LED array](http://e2e.ti.com/group/universityprogram/students/m/students_repository/664650.aspx) (called the Very Large LED Array, or VLLA for short). Since its inception it has been a fixture of many parties and events. Earlier this year Ben decided to completely redo the array. He used flexible RGB LED strips mounted on a plywood frame painted black, with two [Teensy microcontroller boards](https://www.pjrc.com/teensy/) as the brains. A dual USB connection carries images from a computer to the display.

To aid its use as a party utensil, Ben wrote a visual DJing application in Java that allows premade audio-responsive patterns to be combined and swapped on the fly. He made the interface for patterns fairly simple, so that other people (like me) could pick it up and develop effects for the VLLA.

The other night there was a party where we live, and the VLLA was set up above the dance floor. Imagining accolades from a wowed captive audience, I decided that I wanted to write a new pattern for it. Remembering [one of my favorite C64 demos ever](https://www.youtube.com/watch?v=L8onlB0F1_A), I knew what I wanted to make the pattern do. There's a section of the demo where the data from the first side of the floppy disk has been exhausted and some time needs to be wasted while the person running the demo takes the floppy out, flips it, and puts it back in. While that operation is happening, the demo is running a pretty 3D effect, where a voxelated malicious panda (one of the demo's motifs) rotates:

<iframe width="640" height="390" src="//www.youtube.com/embed/L8onlB0F1_A?start=310&end=330" frameborder="0" allowfullscreen></iframe>

I love that effect because it's both technically interesting and satisfying to watch. Also, although coding this effect on the C64 would be a real challenge, the speed of modern hardware means that even a naive approach will work. Ease of implementation was important because I wanted to finish the effect before the party started (or at least before it was over).

Coding
======

For graphical effects like this I enjoy prototyping using [Processing](http://processing.org/). Luckily, Processing uses Java and the VLLA visual DJ uses Java, so I knew I'd almost be able to just copy and paste the results from prototyping in Processing and have it work on the VLLA.

## 2D + 1D = 3D

Although the panda effect is in 3D, and 3D is usually hard, several visual limitations simplify the problem greatly. The panda is only seen from the side, and is rotated about its exact center. This means that if I can figure out how to render a side view of a single layer of panda voxels, I've come up with a solution for the whole effect.

My approach for rendering one layer of voxels is to start out with a square 2D matrix of color values big enough to hold the largest slice of the full 3D model. Then for every pixel in the corresponding slice of the screen I cast one ray through the 2D matrix using [Bresenham's line algorithm](http://en.wikipedia.org/wiki/Bresenham's_line_algorithm). When the ray hits a non-black color value in the matrix it stops and returns the color, which is then drawn into that ray's pixel. Rays that escape the matrix return black.

By casting the rays from further back and rotating their starting positions and headings I can rotate the view of the voxel layer. To give a better 3D effect I made the colors darker for longer rays, which gives some illusion of shadows.

Repeating the raycasting for every layer builds up the full 3D image. The raycasting is an expensive process that I didn't want to try to optimize (I wasn't feeling very mathematical that night). So instead I cached the result of one run of raycasting for every possible rotation, and then just looked up the cached result when drawing. This made the effect run at any speed I wanted, with the cost of a few hundred milliseconds of lag when the effect loads (inconsequential).

## Getting the Panda Model

<style>
    img#panda {
        width: auto;
        height: 128px;
    }
</style>

<img id="panda" src="http://hackniac.com/images/panda/panda1.png">
<img id="panda" src="http://hackniac.com/images/panda/panda2.png">
<img id="panda" src="http://hackniac.com/images/panda/panda3.png">
<img id="panda" src="http://hackniac.com/images/panda/panda4.png">

I wanted to mimic the original effect as closely as possible, so I had to get the 16x9x16 3 color voxels making up the panda in the demo. Initially I had been generating simple shapes with math to have something to see while I tested the rendering code, but I added a bit of code to generate layer matrices from a huge 16x(9x16) integer array. I spent an hour plugging voxels into this array by hand while playing the original panda effect on loop, but it became apparent that I wouldn't finish before the night was over.

Looking for a quick hack to speed things up, I downloaded the Youtube video and stepped through it frame-by-frame in VLC. I made the 4 pixel-perfect images of the panda above, showing each of its sides dead-on. Then I wrote an [awful Python script](https://gist.github.com/jmptable/11151410) that uses PIL to go through two of the images showing orthogonal views (front/back with left/right) and spit out a Java array with positions filled in where absolutely no voxel could be (if a pixel is the background color, then every position in front or behind it is empty). This narrowed the problem down a lot and allowed me to fill in the voxels much faster. After another hour I had a reasonable approximation of the panda. Unfortunately there's some kind of asymptotic curve of difficulty on filling in the voxels, so that getting the very last ones right is extremely difficult, because rotation of the model in the video must be watched very closely for clues about the 3D shape.

Results
=======

I finished [the effect](https://gist.github.com/jmptable/11151665) at 2 AM, right when the party ended. Oh well. I tried it out on the real VLLA the next morning. Unfortunately the color profile of the VLLA does not match my computer's LCD screen. The brightness of the color channels are not in sync, and they do not respond linearly. This muddles the image and makes it hard to discern the details.

<iframe width="420" height="315" src="//www.youtube.com/embed/Kejw1KzkGdc" frameborder="0" allowfullscreen></iframe>

In Processing it looks like this:

![Processing](http://hackniac.com/images/panda/processing_panda.gif)

And in Ben's visual DJ software it looks like this:

![VLLA simulation](http://hackniac.com/images/panda/vlla_sim_panda.gif)

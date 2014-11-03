---
layout: post
title: "tiny_miasmata"
description: ""
category: "old"
tags: []
---

![](http://www.hackniac.com/images/posts/tiny_miasmata/demomite_play.gif)

Tiny Miasmata takes advantage of what is available within those strict limits. The game is a stripped down version of a PC game that I've been working on in Ruby, simply called Miasmata. It was very challenging to manage the basic aspects of the game within the limited hardware and the limited development time available to me, but also lots of fun.

It is a side-scroller. The player can walk around and jump in order to navigate the world, which is composed of 8x8 pixel tiles. Only one tool is available to the player to use to interact with the world: corruption. By hitting the B button the space in front of the player is blasted with random data, giving uncertain results. Sometimes it will change the world in a way that the player wants (cutting through the tree in the picture above), and sometimes it will cause problems. Because of that it makes for an interesting game mechanic, forcing the player to be conservative with its use. The only goal to the game is finding The Enemy wherever he is out in the world and killing him by through corruption.

A lot of work went into making this demonstration of my software skills. Several challenging problems had to be overcome in order to get it working, and it had to be done very quickly. Demomite was built in a Sunday and Tiny Miasmata was finished by the end of the following week. This description covers the most significant challenges I encountered during this project, but I encourage you to take a look at the code yourself to see its full complexity (link at the bottom of this post).


### Sound

The black and white graphics are very basic, but a little bit of sound adds some richness and color to the world. I managed both music and sound effects by taking advantage of two very useful features of the Attiny2313 MCU: hardware pulse-width modulation (PWM) and timer interrupts. The PWM allows me to output nearly any audible frequency continuously without wasting any CPU time. That means that I can play a tone while doing other stuff in the game, but a solid tone would get annoying very fast and is not very interesting, so I used the other feature, timer interrupts, to add some variation. An interrupt allows an external event, in this case a timer, to pause execution of the current code to execute it's own code associated with it and then resume execution of the original code. The interrupt code I wrote for Tiny Miasmata simply updates the tone playing via PWM from a series of values stored in memory that constitute a "song" (quotes because I am not a musician, so it sounds fairly horrible). This all means that I can easily play some music in the background without worrying about dividing CPU time between the game and the music.

Music: [song](http://www.hackniac.com/blog/wp-content/uploads/2012/02/song.wav)

However, the sound effects are handled in a slightly different way because of their nature. The two sound effects I have included are one for when the player attacks, and one for when the player dies. In both cases I found the best strategy was to modify the PWM by both the timer interrupt and the CPU at the same time, because for both I was going for a random sound that would give the sense of corruption, the theme of the game (and it was easiest and took up the least space).

Effect #1: [corruption](http://www.hackniac.com/blog/wp-content/uploads/2012/02/corruption.wav)

Effect #2: [death](http://www.hackniac.com/blog/wp-content/uploads/2012/02/death.wav)


### World

In terms of complexity, the system that handles the map for Tiny Miasmata is the most impressive part of the project. A key aspect of the full game is a nearly limitless world. On the PC I accomplish that through procedural generation using a random seed, but that approach is much more difficult on the Demomite because of the limited resources. I tried a few approaches that would generate a map from the program data itself as the seed, but the results were never satisfactory and took up a very large space. I settled on a simpler strategy that actually proved to be much more flexible - simply loading a pregenerated map from memory. To tell the truth it was a bit of a disappointment to have to change course (I really love the concept of procedural generation), but it provided fun new challenges to surmount.

**Storage problem**

The foremost problem was the matter of storage. I only had 2K of program flash to work with, which is primarily needed to store the code. The paltry 128 bytes of RAM was about one fourth used up by the stack, and the EEPROM is too slow, small, and complex to utilize for the maps. I decided that I would take advantage of both the RAM and the program flash, splitting the task between both in a compromise that would use up less space while being very computationally efficient.


**Compressing the map**

To store the actual map I developed a simple compression algorithm. It came about after researching the modern types of compression algorithms that are used everyday, but it was not based on those, just inspired by them. It's a simple kind of indexing system. Each "screenful" is stored separately, and is constrained in the following way to reduce the storage size: Only 4 tile types can be on a single screen, which means that each tile can be expressed as two bits. The screen is 10x6 tiles in size, so there are 60 tiles on each screenful and it only takes 15 bytes to store them. However, I designed more than 4 tiles into the game. To get around the 4 tile-per-screenful limit I added a header at the beginning of each screenful. The header indexes a two byte value in a "group table". Each entry in the group table is a combination of tiles, which allows the (up to) 4 tile types used on a given screen to be looked up and decoded. Altogether this means that each screenful takes 16 bytes, which makes the indexing math beautifully simple, and the only annoying bit is that there must be a small group table floating around somewhere to be used to decode the map.


**Decompressed in RAM**

Using this compression scheme allowed me to fit a 4x3 screen map (720 tiles) into the memory I had left over after writing the game logic. Unfortunately, the compression makes it very difficult and slow to interact with the map from the perspective of the game logic. My solution to that was to decompress a screenful into a section of RAM to interact with it. In its decompressed form it is composed of 1 nibble per tile (there are less than 16 tiles in the game so this is sufficient), bringing the space needed to 30 bytes. This simplifies programming collision detection and other things that need to look at the map a lot because it turns into a simple matter of indexing the correct byte and then isolating the value of the correct nibble.


### Map editor

[![](http://www.hackniac.com/blog/wp-content/uploads/2012/02/mapper.png)](http://www.hackniac.com/blog/wp-content/uploads/2012/02/mapper.png)

So this compression stuff is all well and good from the point of view of the game, but what about from the perspective of the guy who has to generate the maps (namely, me)?  I could not practically create a table of values by hand to express a map in a way that could be assembled into the binary and decompressed by my map routines, I needed a way to easily edit maps and compress them automatically. To accomplish that I wrote an ugly Ruby script (included with source-code) that takes an image as input and outputs a text file with the group table and a series of tables for each screenful. From there I can just include it into the project within my assembler and it ends up in the binary while being easily pointed to by the rest of my code. I also took advantage of the Ruby game library I've been using for the PC version of Miasmata, called Gosu, to give the option of displaying a scrollable preview of the compressed map (seen above).


### Collision Detection

Strangely enough this is where I had the most challenging code to write. The techniques for collision detection I used at first broke later on and I had to take another shot at the problem. Those early attempts were based on the positions of the tiles, only checking to see if something was in a given tile location. The later collision detection code is not at all complicated, just a little subtraction to check for collisions between squares, but for some reason it took a lot of effort to produce. I think that it might just be due to my poor ability to imagine how the overlapping objects corresponded to the math. In the end the solution I came up with works reliably, but it's fairly clutsy. If I had the time to fully rewrite it I would expand its capabilities to objects that can move faster than 1 pixel per frame and do pixel-perfect collision or collision with bodies that can rotate. That would greatly improve the feel of the game, because the physics could be more natural, but would be much more challenging to code.


### The Enemy

[![](http://www.hackniac.com/blog/wp-content/uploads/2012/02/demomite_play_enemy1-300x255.jpg)](http://www.hackniac.com/blog/wp-content/uploads/2012/02/demomite_play_enemy1-e1328138518322.jpg)

I dug myself so deeply into the challenges associated with the game world and bringing the player to life within it that I neglected one of the most important part of any story, whether it is told by a game or not - the conflict. The player could move and jump and explore the world, but had nothing to do. I'll admit that this part was almost an afterthought. When I reached the point of adding an enemy for the player to fight I was almost out of time to work. I basically copied the player's code exactly and added a tiny bit of intelligence.

To simplify things there is only one enemy. He looks exactly like the player. If the enemy sees the player it will move towards the player and kill him or her on contact. Even though there is only one enemy, to the player it seems like there are many, although only one at a time. When the enemy dies he is recycled and spawned anew in another section of the world.

[![](http://www.hackniac.com/blog/wp-content/uploads/2012/02/demomite_play_death-300x258.jpg)](http://www.hackniac.com/blog/wp-content/uploads/2012/02/demomite_play_death-e1328138469879.jpg)

As a matter of necessity the player needs a way to fight the enemy. To that end I created the tool of corruption, which is the central theme of Miasmata. The world that the player inhabits is corrupted by the Miasma, but the player can do corrupting as well. In the PC version of the game this ability can be used to destroy as well as create, although which one is left up to chance. In that sense the power of corruption in Tiny Miasmata is much more blunt. The player can use corruption to randomly change the map nearby or kill the enemy. The changes are not saved and the enemy is never truly dead. Any use of corruption messes up the image on the screen and therefore makes it harder to tell what is going on.

### Conclusion

This is the most difficult software project I have ever taken on (or at least that I have gotten to some semblance of a finished state). It was a really great challenge, fun and intense. I wish I could have put more of myself into it, but the usual anchors of responsibility to school and living held me back as usual. I'm going to keep exploring what I can do with this fun little platform of mine, there is a lot of potential hiding in its diminutive hardware.

[Source code](http://www.hackniac.com/blog/wp-content/uploads/2012/01/TinyMiasmata.zip)

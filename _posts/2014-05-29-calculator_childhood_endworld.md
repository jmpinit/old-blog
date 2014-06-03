---
layout: post
title: "calculator_childhood_endworld"
description: ""
category: "subpost"
tags: []
---

# METEORS

![METEORS](http://hackniac.com/images/posts/calculator_childhood/METEORS.gif)

Drops a lot of meteors at once and then simulates their collisions with the ground.

# ARMAGED

![ARMAGED](http://hackniac.com/images/posts/calculator_childhood/ARMAGED.gif)

Simulates Armageddon. Generates a terrain, then fills it with buildings in caves. Then it simulates the collapse of the generated world on a per-column basis. To carry out its chaos, it uses several helper programs:

* _GENMAP_: Draws/generates the terrain.
* _GENMAP2_: Slightly faster terrain generation that uses line drawing instead of pixel-by-pixel drawing.
* _CAVE_: Draws the caves by picking random positions and then removing randomly sized and vertically centered lines. Each subsequent line size differs by at most 1.
* _HUTS_: Generates the buildings by picking a random number of stories and then drawing upside-down Us on top of one-another.
* _METEOR_: Drops a meteor on the world. The meteor is represented by a pixel that crawls down the screen from the top. When it hits a black pixel it "explodes" and erases a half-circle below it.
* _METEORS_: Drops meteors on the world using METEOR.

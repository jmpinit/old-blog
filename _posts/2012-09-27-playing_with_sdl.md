---
layout: post
title: "playing_with_sdl"
description: ""
category: "old"
tags: []
---

![perversion](http://www.hackniac.com/images/posts/3d-conway/3dconway.png)

I am learning how to use SDL. This afternoon I wrote the code that generated the image above. It is a mirrored wireframe height map. On the surface is a simulation of Conway's Game of Life. A bump indicates life and flatness indicates death.

The renderer is my own. I am not using OpenGL, just [SDL_Draw](http://sdl-draw.sourceforge.net/) to draw the lines. Check out the code [on Github](https://github.com/jmptable/3d-conway)!

![life's a lonely game](http://www.hackniac.com/images/posts/3d-conway/3dconway2.png)

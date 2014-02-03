---
layout: post
title: "<insert title here>"
description: ""
category: "old"
tags: []
---


I was still hungry after the success with displaying images and characters, so I wrote tilemap code too. The tilemap is currently stored in PROGMEM, which is kind of silly because I'm sure you would want to have it in RAM to do anything useful for it (like space invaders as I originally intended), but hey, that's what you get on a school-night with an icky A.P. history test to study for the next day. With a little bit of modification the tilemap could be stored in RAM. There is _juuusstt _enough RAM to let that work, because the tilemap can be up to 10x6 tiles in size with 8x8 tiles, meaning you'll have just 4 bytes of RAM left after storing the 60 byte tilemap. The library could be rewritten to use maybe 2 bits per tile in the tilemap (allowing 4 different tiles) but that would require packing and unpacking code and blah blah. Maybe when I need another challenge...

[![](http://www.hackniac.com/blog/wp-content/uploads/2011/06/proto_tilemap1-e1308855931545.jpg)](http://www.hackniac.com/blog/wp-content/uploads/2011/06/proto_tilemap1.jpg)

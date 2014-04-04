---
layout: post
title: "face recognition hw"
description: ""
category: draft
tags: []
---

![dissolving](http://hackniac.com/images/face_hw/dissolving.gif)

![approximating some guy's face](http://hackniac.com/images/face_hw/approx.gif)

![approximating the face of George Bush](http://hackniac.com/images/face_hw/approx_bush.gif)

Here's the (bash) command I used to put the generated images together into a GIF.

```
convert -delay 8 -loop 0 $(ls *.jpg | sort -n) dissolving.gif
```

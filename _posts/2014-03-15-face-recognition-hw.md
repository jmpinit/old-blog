---
layout: post
title: "face recognition hw"
description: ""
category: draft
tags: []
---

Here's the (bash) command I used to put the generated images together into a GIF.
    convert -delay 8 -loop 0 $(ls *.jpg | sort -n) dissolving.gif

![dissolving](http://hackniac.com/images/dissolving.gif)

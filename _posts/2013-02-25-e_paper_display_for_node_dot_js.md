---
layout: post
title: "<insert title here>"
description: ""
category: "old"
tags: []
---


I got a Nook Touch e-reader second hand, rooted it, wrote an android app for it, and wrote a tiny Node.js server to talk to the app so that I could have a remotely-controlled low-power monochrome display. The server sends bitmaps to the Nook using Sockets, so any arbitrary B&W image can be displayed on the Nook remotely, as long as it is connected to the internet.

<!--more-->

Uses
====

* On my door (in a college dorm) it can let people know if I am awake to be pestered or not. Also useful to let people know where I am, if I feel like divulging that information.
* On my wall it serves as a general info display, telling me the status of my roommates (resurrected servers) and if I have email. A tiny bit of JS added to the Node.js server lets it display any arbitrary data stream.
* A fun thing to play with. I'm enjoying writing little bits of code to draw silly things on the screen. It's nice to put up some slowly changing graphic and watch it evolve out of the corner of my eye. More interesting possibilities than a static work of art, in my opinion.

Backstory
=========
A club called MITERs here at MIT organizes a flea-market for electronics called Swap Fest. I've picked up great stuff for just a few dollars everytime I've gone. One of the thing I got last time was a slightly used Nook Touch e-reader. I'd always wanted something with an e-paper display to play with but I didn't really have anything in particular in mind for it. After a month of using it as an e-reader I took it apart, lost interest, and let it sit in a pile of other junk until this past weekend.

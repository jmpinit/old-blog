---
layout: post
title: "bug_helicopter"
description: ""
category: "old"
tags: []
---


[![](http://www.hackniac.com/blog/wp-content/uploads/2012/09/2012-07-24-21.13.11-1024x726.jpg)](http://www.hackniac.com/blog/wp-content/uploads/2012/09/2012-07-24-21.13.11.jpg)

While I was in Washington I had access to a bunch of IR controlled toy helicopters. I took one and turned it into a bug-like thing by removing the original shell and adding a new cardboard one put together with tape. It was a mostly cosmetic change, but I was also hoping for it to be functional because it meant the machine wouldn't take off straight up and down. I thought the forward-leaning stance would lead to the ability to make hops, but it turned out to mostly just cause problems with take-off.

<!--more-->

The thing flew backwards better than forwards and couldn't land without falling over, but it was a lot of fun to make and play around with. I also tried new orientations for the rear rotor without much success.

Playing with the electronics I figured out how the stabilization system on these things works. The rear rotor isn't used for counter-rotation like in a conventional helicopter, instead it is used for tilting the helicopter  to move forward and backwards. To prevent the machine from rotating there are two sets of blades spinning opposite of each other. An accelerometer is used by the control board to control the magnitude of a difference in speeds between the blades, which allows the helicopter to keep facing in one direction.

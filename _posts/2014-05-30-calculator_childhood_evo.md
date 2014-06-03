---
layout: post
title: "calculator_childhood_evo"
description: ""
category: "subpost"
tags: []
---

Evolutionary Algorithms
=======================

I made a whole slew of these, but none of them worked when I came back to make GIFs of them, so a short description from memory is all I've got.

In most of them the simulation involved a little character trying to run across as far as possible across a hilly terrain. The characters could move left or right and jump. Their genetic code kept track of their pattern of movement. Usually it was just a series of values stored in a list, like 1 for move left, 2 for move right, etc. Initially the genetic code of a population was completely random. Then each individual was allowed to make an attempt at crossing the terrain, and their score was recorded as the horizontal distance in pixels that they moved. N of the best individuals were used to generate the next population by randomly making random changes, and randomly copying or swapping values between individuals (mutation and inheritance, respectively).

None of these programs were very effective. They were always extremely slow (each individual took upwards of 30 seconds to test), so I'd let them run all day on my calculator in my pocket as I went to class and then check for results on the bus ride home. They'd usually either crash at some point or produce individuals with abilities marginally better than random movement.

I think that they performed poorly because of many separate problems. The population and "winner" counts were chosen arbitrarily, the mutation was not implemented well, I think the scoring was buggy in some, and the "genetic code" should have described intelligence rather than specific motion.

---
layout: post
title: "calculator_childhood_games"
description: ""
category: subpost
tags: []
---

BASCLASH
========

![BASCLASH](http://hackniac.com/images/posts/calculator_childhood/BASCLASH.gif)

In this game two TIBASIC programs control robots that try to navigate a 2D top-down map and kill each other. The game runs one program and then the next. After each program runs it looks for a value in the Ans variable to know what action to make the robot take. By using this communication strategy the game can enforce world collisions and other game rules. For it to work correctly the robot programs are disallowed from using certain variables. If they wanted to the robot programs could change anything about the game, like instantly making them the winner. For this reason modifying the game's variables is against the rules.

BOMIO
=====

This is probably the best game I ever made on the calculator (not that I tried very hard). In the game the player controls the letter __T__. They can jump, move left/right, and lay time-delay bombs. The letter __A__ is an AI who tries to chase after the player to kill them (touch them). The player's goal is to avoid __A__ until they can kill him with their bombs. In the course of the fight the environment is changed by damage from the exploding bombs.

![BOMIO](http://hackniac.com/images/posts/calculator_childhood/BOMIO.gif)

Dying:
------

![BOMIO death](http://hackniac.com/images/posts/calculator_childhood/BOMIO_died.gif)

Map Saved in Picture:
---------------------

![BOMIO map](http://hackniac.com/images/posts/calculator_childhood/BOMIO_in.png)

MINER
=====

A 2D, side-scrolling Minecraft clone that I never finished. It used one of the TIBASIC helper programs to do sprite operations. The only aspect that I completed was a level editor.

![MINER](http://hackniac.com/images/posts/calculator_childhood/MINER.gif)

MAPPER
======

A program for editing game maps stored in matrix variables.

![MAPPER](http://hackniac.com/images/posts/calculator_childhood/MAPPER.gif)

RACER
=====

![RACER](http://hackniac.com/images/posts/calculator_childhood/RACER.gif)

Race a pixel down a winding track. If you touch the sides you die. Used an assembly program to shift the screen down each frame, but was otherwise written in TIBASIC.

PIXED
=====

![PIXED](http://hackniac.com/images/posts/calculator_childhood/PIXED.gif)

Extremely simple side-scrolling platformer. Try to get to the right side of the screen by moving and jumping. Picture variables were used to store the maps, so the calculator's built-in drawing tools could be used to create them.

MIASMATA
========

![MIASMATA](http://hackniac.com/images/posts/calculator_childhood/MIASMATA.gif)

Unfinished calculator port of my Demomite game [Tiny Miasmata](http://owen-t.me/old/2012/02/02/tiny_miasmata.html).

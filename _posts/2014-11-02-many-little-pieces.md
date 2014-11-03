---
layout: post
title: "many little pieces"
description: "a hackathon game"
category: "software"
tags: []
---

![](http://hackniac.com/images/posts/many_little_pieces/mlp.png)

## Overview

[Many Little Pieces](https://github.com/jmptable/many-little-pieces) is a small, unfinished multiplayer web game designed to combine the fun of [MUDs](http://en.wikipedia.org/wiki/MUD), [minimalistic programming](https://www.youtube.com/watch?v=7lcQ-HDepqk), and [Internet serendipity](http://www.yourworldoftext.com).

The world of the game is an infinite 2 dimensional grid of text that is shared by every person playing the game. Initially the world is completely random, with characters placed in sporadic clumps. As a player you can collect and rearrange the text that makes up the world however you like. Just by moving text around letter by letter you are able to communicate with other players or set up ASCII art structures to inhabit. But the letters can be used in a much more powerful way: to write code that automatically changes the world.

## Programming the World

The world of MLP operates according to unique laws of physics. Energy flow follows the contours of text according to the rules of The Language. To wield great power, one may learn The Language and use it to direct the energy of the world and produce change.

Put simply, by collecting text and using it to write computer code, players can build machines that interact with the game world and change it. The concept is copied from multi-user dungeons, where players are able to add whatever they want to the game world by using a special programming language. But in MLP the world is the code and code is the world.

## Machines

Wielding The Language on the text of the world produces machines with form and intelligence. For example, text can be instructed to exclude anything else from its location, creating a wall. Or text can be instructed to exclude anything on the condition that it is not passed a code, creating a door.

More complicated machines can roam the world and collect text on their own, multiplying the efficiency of a single player. And they can be used to ferry information over long distances to other players.

While the purposes that machines could be put to is theoretically unlimited, there are limits on their operations. Every machine consumes a portion of the player's finite energy at a fixed rate. Without energy the machine cannot operate.

There is a fixed amount of energy in the world. It is proportional to the speed of the server that the game runs on. Each player is guaranteed a fraction for use by their machines.

## The Language

Every little piece of code must be collected from the world before being assembled into a working program, so it is very fortunate that the syntax of The Language is terse. It is based on the real language called [Forth](http://en.wikipedia.org/wiki/Forth_(programming_language)). Forth looks weird, but it is very efficient and simple.

---
layout: post
title: "incomplete_flash_game_hackwire"
description: ""
category: "old"
tags: []
---


[![](http://www.hackniac.com/blog/wp-content/uploads/2011/09/hackwire_plug.png)](http://www.hackniac.com/blog/wp-content/uploads/2011/09/hackwire_plug.png)

Wireman, the most dangerous hacker in Robot World, has finally been caught. For the protection of robot society he is imprisoned in a complex within an asteroid floating far away in space, his mind transferred to a computer that has no connections to the outside world. A skeleton crew maintains the asteroid prison and makes sure their dangerous prisoner does not escape. The crew includes an old, and dim-witted, cleaning robot. After a short time in his prison Wireman hatches a plan to escape. His only connection to the outside world are some indicator lights on his body's control panel, but for the craftiest hacker, Wireman, they are plenty to carry out his plot. When the unintelligent cleaning robot comes to tend to the area around Wireman's computer he sees the that all of the lights are blinking a self-destruct countdown. Alarmed, the janitor bot connects to the controls to try to stop what he thinks is his imminent death. Immediately Wireman hacks the janitor and they swap bodies. Off Wireman goes to escape the asteroid and reclaim his place as hacker king!

<!--more-->

I like hacking and I like robots, and I like programming and I like money. So naturally I would want to combine them, and I got close to doing so with this flash game that I started developing during last summer. I called it Hackwire. The intention was to make it in a few weeks of intense work and then get it sponsored on a flash game website and make some money to spend on my other projects. It didn't turn out that way mostly because it was only my second attempt at flash game development, but I succeeded in making at least a simple demo and learned quite a bit about the process.

Below you can play the demo of the game that I created, peruse both my [Flashdevelop ](http://www.flashdevelop.org/)project and source code for the game, and take a look at the notes that I took during my thought process in developing it.

[edit: sorry, fixing slideshow system]

[Code to peruse.](http://www.hackniac.com/blog/wp-content/uploads/2011/09/Hackwire.zip)

In the demo you can move around the small map and swap bodies with the enemies present in it. They all have very stupid AI, simply moving randomly. The security bot in the top portion of the map cannot be hacked into with your hackwire, because he doesn't have a connection port. Try hacking into the computer prison in the lower left and then controlling him; I like how he turned out. A look through the code for the game will clear up exactly how that stuff is implemented. I try to make my code as elegant as possible, much of my time is spent thinking philosophically about how game objects are related (probably why I never finished the game), so it might be interesting to peruse.

**Controls:**

* Move - A, D
* Jump - W
* Hack - Spacebar

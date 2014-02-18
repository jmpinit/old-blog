---
layout: post
title: "deep_magic_progress_update_0"
description: ""
category: "old"
tags: []
---


Today I began project Deep Magic in earnest. I found an old copy of the Z80 instruction set that I had printed out a few months ago and then started printing out the ti83plus include file. I quickly abandoned the idea of printing out the entire include file, it is 84 pages long and so too expensive for my home printer. Maybe I'll print the whole thing sometime on a printer at school, but in the meantime I'll just use the table of RAM locations that I cut out and printed.

My plan for completing the hack is as follows: First I will write an assembler by hand on paper in regular z80 assembly, then I will assemble it by hand into a hexadecimal listing that I can type into the calculator. I will take advantage of the hexadecimal string to program-binary function built into the calculator's operating system to get the program into an executable format. Once I've got that compiled and working, which will be no small feat even on its own, I will move on to constructing simple programs to manipulate the calculator's link port in various ways. Before I do anything with the TI Navigator I will first verify that my routines work with other regular TI calculators. When I can send and receive data in the Texas Instruments protocol I'll start probing the Navigators.

Beyond that point I don't really know what path I will take. In a perfect world I would be able to find the exact way that the Navigators take instructions from the computer just by sending out carefully chosen data and listening for the response, but more realistically it will require some snooping of the data being passed to the Navigator from the computer. That may be hard to do without breaking any school rules, but maybe I can convince my Calc teacher to let me indulge in direct research.

No matter the method that I use to discover the secrets of the Navigators, what I do with those secrets will remain the same. After tricking the Navigator into thinking that it is connected to a computer when it is really connected to my calculator I will be able to send arbitrary data over it and engage in any of the activities that my teacher can and possibly others that haven't been fully exploited in the PC software for the system. Games would be really cool, but I think that my favorite thing to do with my new-found powers would be to make a miniature version of the internet using the Navigators. With the right organization simple websites could be hosted by calculators serving as servers, or external hardware could be plugged in to form a mainframe with other calculators being the terminals. The possibilities are really endless. I'm happy to have a full year of school to try to exploit them.

---
layout: post
title: "multicore_microprocessor_simulator"
description: ""
category: "old"
tags: []
---

![](http://www.hackniac.com/images/posts/multicore/os_load.gif)

This project is a simulator for a novel RISC microprocessor called Multicore with multiple processing cores and an assembler. Multicore has memory mapped I/O devices including a terminal and disk drive. Everything is written in Java and I put a lot of effort into making sure that it is easy to expand. It has also been fairly well tested, and I've written several demonstration programs in assembly language for it. The entire thing can be downloaded from the link at the end of this post.

[![](http://www.hackniac.com/blog/wp-content/uploads/2011/12/multicore_layout1.jpg)](http://www.hackniac.com/blog/wp-content/uploads/2011/12/multicore_layout1.jpg)

This project came about because I had the option to take discrete math this year at my high school and I had an empty spot in my schedule, so I took advantage of it. It's not as in-depth as I was hoping, but it has done well to introduce me to many useful ideas in the field ranging from graph theory to scheduling. Recently we had to complete a project utilizing schedule theory and present it to the class. The format was laid out very narrowly and did not allow for much creativity past picking tasks to schedule. Luckily for me my teacher is very flexible and knows about my interests because she oversees my independent study this year. She approached me with the opportunity to combine the class project with my independent study, and I gladly accepted it.

My independent study involves creating a network of independent processors. One application for it that I am working on is dividing up tasks over the entire network so that no individual processor feels all of the strain. To divide up tasks among the processors intelligently I need some kind of scheduling algorithm, so the discrete math class project meshed perfectly with the project. Since I did not have much actual hardware to run a scheduling algorithm on I decided to write a simulator for an imaginary microprocessor with multiple cores to run the algorithm on instead. I've been infected with the urge to write a microprocessor emulator for a long time so that's the main reason why I went ahead with this idea that isn't perfectly in line with my independent study. I have attempted writing such an emulator before, but I have not been successful until this project because I lacked the programming skill.

My original plan was to implement a full operating system to run on the microprocessor that would schedule tasks for the cores in real time. I had to abandon that ambitious plan because of time constraints, although it's perfectly possible to do and I think I'll end up remaking it on a real microprocessor later down the road of my independent study. Instead of writing a full O.S. to demonstrate application of scheduling theory on my sim I wrote a Java program that takes a mathematical expression as input, parses it into a task tree, and then outputs assembly code to evaluate it efficiently using all of the cores of the processor. It's a very Rube-Goldberg-esque system (hence the title of my presentation being "The World's Most Complicated Calculator), but it shows proper application of the theory and works so I am satisfied with it. Overall this project was extremely fun to do, and I am definitely going to keep the using the simulator as a programming toy (why so few enjoy assembly programming confuses me).

Most of the project came together over my Thanksgiving break, but it also extended to the weekend afterwards. Because it became part of my independent study project I had to log the hours, so I know that overall it took 46 hours and 45 minutes to make, including putting together the presentation for my class, which is below.

Note: Although it is written in Java I developed it using [Processing](http://processing.org), so if you want to run it please use that. Also, it uses some hard-coded directory strings to load programs, so those will need to be changed if you want to get it to run properly. Those strings can be found in the main pde file and in the DiskDrive. Please use it however you wish. Just keep in mind that I would absolutely love to hear what you think of it or how you use it.

[Code and documentation](http://www.hackniac.com/blog/wp-content/uploads/2011/12/Multicore.zip)

[Mathematical expression evaluation code generator](http://www.hackniac.com/blog/wp-content/uploads/2011/12/Scheduling.zip)

---
layout: post
title: "6_270_robotics_competition_mit"
description: ""
category: "old"
tags: []
---


To download the code visit the project's [page on GitHub](https://github.com/jmptable/vs-robot).

### Overview

Our robot's code is divided into these main sections:
	
* Task management - choosing the most advantageous strategy at any given time.
* Task completion - carrying out the actions needed to successfully complete each task.
* Navigation - moving the robot around the arena.
* Sensing - gathering accurate information about the robot's surroundings.
* Glue and support - math, debug, calibration

Thankfully JoyOS implements a simple round-robin scheduler that allows easy threading, so it was straight-forward to keep these sections independent of one-another. In addition to the main initial thread there is the thread named Sensor and the thread named Navigator.

**Sensor**

Information from the VPS, motor currents, contact switch states, and encoder values are fused together into a best guess of actual robot state at each moment. Some information is fused from multiple locations for robustness. For example, the Sensor detects when the VPS is sending invalid data and switches to relying on dead-reckoning (via the wheel encoders) for position to maintain accuracy. Because of the filtering that the Sensor provides the rest of the system does not need to deal with and validate raw information.

It greatly simplifies much of the code, because access to current sensor data is as simple as referencing a member of the "bot" structure.
	bot.x and bot.y //current location of robot, regardless of VPS status
	bot.territory //current territory that the robot is located in
	bot.velocity //the current forward speed of the robot
	bot.heading //the current absolute (in VPS coordinate system) heading of the robot. fusion of VPS info. and gyro measurements
	bot.obstructed //whether the robot is physically stuck. inferred from motor current draw, change in location versus target speed, or contact switches


**Navigator**

JoyOS provides easy control and direct control of the robot by setting motor velocities (or positions, in the case of servos), but did not have enough control built in for our needs. To facilitate higher-level behavior like smooth acceleration, driving straight, navigating between points and territories, facing points, and more we created the Navigator. The highest-level (where the AI is) simply asks the Navigator to carry out such tasks and they are done, hiding that unnecessary complexity from the AI code.

One of the lectures for 6.270 was on the subject of control systems, and the concept of a PID loop was explained. We implemented a generalized PID system inside of the Navigator, and it found application in keeping the robot driving straight, turning smoothly, and maintaining the correct distance from the center of the arena while driving between territories.


### Debug System

Testing was extremely important for the 6.270 competition. The code can be beautiful and compile fine, but it will fail 9 times out of 10 when tested on the real hardware. Unfortunately, because of the large number of teams and single VPS system testing was slow and difficult. Test runs had to be kept short so other teams would get their turn, and waiting in line meant no work would get done.

To address this difficulty we used a fairly complex testing system. It hinged on the addition of a serial-bluetooth module, which was connected to the second hardware UART of the Atmega128 on the HappyBoard. With that in place we had easy two-way communication between our development machines and the robot while it was running, with no cable to get tangled or otherwise limit the motion of the robot.

Getting data off the robot was made a little easier by this modification, but its most important advantage was the communication it allowed in the other direction. The development cycle for Duck was much slower than a pure software project because of the need to flash changes to the AVR microprocessor on the HappyBoard and then reset it. Each time a change was made it took 15 to 25 seconds just for the change to be flashed onto the chip. Changing code while taking a turn with the VPS was out of the question.

But with the two-way bluetooth connection we could make tweaks to the robot during a test. A terminal was written to be used over the connection. It supports several powerful debugging features. The robot can be remote-controlled, emergency stopped, have its sensor values read, and have the current values of variables viewed or changed.

The debug system is interrupt-based, so it is nonblocking and does not interfere with the operation of the robot. For it to work the programmer has to use the macro WATCH(var, type), which lets the debug system know where the value of interest can be found and what can be done with it. This trick was invaluable for tuning the PID loops and doing sanity checks ensuring the robot's view of the world was what we thought it should be.


### Activities

The task management system weighed the potential point value of completing each of the following activities in each one of the six territories, and picked the current most valuable one in-between requesting their completion. In addition to potential points the task manager considered how far away the territory in question was and whether it contained the opposite team's robot, or whether the robot was already in the territory.

* Exploring - driving through territories in the first 10 seconds counted them as explored and awarded points
* Capturing - spinning a gearbox in the right direction in an uncaptured territory captured it for our team, awarded points, and allowed that territory to be mined
* Mining - driving up to a ball dispenser and flipping its lever dropped balls into the robot and awarded points for each one
* Dumping - collected balls dropped into the correct side of the center doubled the points awarded by mining them


### Challenges

**VPS lag / Feedback**

Visual Position System information was fairly coarse and unreliable, compared to the other sources of information that the robot had. One major problem that it had was a ~300 ms lag-time. Robot state according to the VPS was always significantly in the past compared to the current robot state, and that had to be accounted for to prevent problems. Initially we navigated without worrying about the lag, but that led to a feedback loop involving the PID controlling our heading and very snakey movement. Eventually we developed a system that used other sensor information to bring the VPS-reported state closer to the present, and that helped to reduce feedback problems, but we never fully eliminated them and they were a continuous source of frustration.

**VPS shift**

The VPS was in development during the competition, and changed significantly. Early on there seemingly wasn't a way to calibrate it to the board, so each day it would be shifted a bit and any recorded coordinates that we had were a little bit off. This caused a lot of frustration because it was very subtle and hard to catch on to. We didn't have a good solution that was robust, so we tried to rely as little as possible on exact stored coordinates.


## UTILITIES

To help debug the robot we wrote two tools. The first was a simple simulator that was helpful in prototyping approaches to movement before the physical robot was constructed. The second tool was a program that graphs information from the robot in real-time. It was extremely helpful debugging navigation towards the end of the competition. Below are screenshots from these two tools to give a sense of their use. The actual tools themselves can be found in the code archive.


### Simulator

![robot simulator](http://www.hackniac.com/blog/wp-content/uploads/2013/02/simulator.png)

The square is the simulated robot, with its front indicated by the line. The red circle is the target that the virtual robot is following. For each prototype approach a new Java class was written that inherited from the Robot class. The Robot class contained methods identical to those in JoyOS, so the code written in a prototype could be pasted directly into the real robot's code and compiled as C with minimal changes.


### Bot Grapher

The empty circles are the important VPS coordinates stored in the robot. Red circles are capture points, blue ones are mines, and the green ones are waypoints (in the center of the territories). The white circle is the location of the robot when logging stopped, and the white line is the path it took. The path is where the robot thinks it went, not necessarily actually where it went.

![circle](http://www.hackniac.com/blog/wp-content/uploads/2013/02/circle.png)

Told the robot to navigate in a circle and maintain its distance from the center using a PID. Lag from the VPS caused feedback that led to the curves.

![not dead-reckoning](http://www.hackniac.com/blog/wp-content/uploads/2013/02/with_vps_1.png)

Here the approach was: turn in place to face the target, calculate the distance to the target, then drive for that distance in a straight line. It was the most accurate method but slow. And sometimes it would glitch and head in a completely wrong direction with no possibility of correction.

![more vps updates](http://www.hackniac.com/blog/wp-content/uploads/2013/02/update_more.png)

Modified version of the previous approach where the robot used its internal gyro to continuously update its heading towards the target. Worked very well except for the glitches at the first two waypoints, which we did not have time to figure out.

![heading update with vps](http://www.hackniac.com/blog/wp-content/uploads/2013/02/en_route_vps_heading.png)

Instead of blindly following the internal gyro reading (which can get out of sync with the real VPS heading) we took advantage of the often-true fact that half-way to our destination we would be travelling straight, so error due to VPS lag would be minimized for the heading. Syncing with the VPS always seemed to make things worse...

![hybrid](http://www.hackniac.com/blog/wp-content/uploads/2013/02/linear_rot.png)

Eventually the Sensor was able to keep track of the rotational velocity of the robot, so we used that as a way to know when the VPS lag error would be minimized. If the rotational velocity was below a threshold we synced with the VPS.

![tracing arena](http://www.hackniac.com/blog/wp-content/uploads/2013/02/trace.png)

This was not the robot's doing. We dragged it around the edge of the arena by hand to check the VPS coordinates that we had stored inside of it.

![failed dead-reckoning](http://www.hackniac.com/blog/wp-content/uploads/2013/02/no_vps.png)

At one point the radio was taken out of the robot so dead-reckoning could be tested. It had worked very well several times previously, but on this attempt it failed miserably. It thought that it was driving around outside of the arena when really it was running hard into the wall.

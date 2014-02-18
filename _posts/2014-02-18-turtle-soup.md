---
layout: post
title: "turtle soup"
description: "Art using turtle graphics."
category: software
tags: [java]
---

![mario test](http://hackniac.com/images/turtle_soup/turtle_mario.gif)

My first problem set for 6.005 (Software Construction) ended with a question asking me to draw "personal art" using the [turtle graphics](http://en.wikipedia.org/wiki/Turtle_graphics) used during the rest of the problems. When submitted, the homework server saves the images produced by everyone's code so that they can be voted on. The person who made the art that gets the most votes wins a prize.

This is the kind of task that gets me very excited to do my homework. I sunk about 10 hours into making the nicest thing I could, both in terms of the output and the source code. I tried a few things that didn't pan out (like a simple ray tracer - the output was 3D but ugly), but ultimately combined a few neat ideas/techniques to draw a picture that I like.

## Hilbert Curve

My approach started out with a neat math concept called space-filling curves, which I had heard about a few days before in the context of [visualing binary data](http://www.youtube.com/watch?v=4bM3Gut1hIk). Basically, I map the pixels of an arbitrary image onto a [Hilbert space-filling curve](http://en.wikipedia.org/wiki/Hilbert_curve), which the turtle then traces. Doing that makes the drawing process visually interesting, and gives me more freedom in the actual art being drawn, because it can just be represented in a normal raster image and not some complex vector format.

## Palette Restriction

One interesting limitation on the image is the limited palette that the turtle can draw with. Only black, blue, cyan, gray, green, magenta, orange, pink, red, and yellow can be used. I wrote [a Processing program](https://gist.github.com/jmptable/8928370) to automatically convert images to this palette by looking at each pixel and deciding which palette color it is closest to:

	int smallest = -1;
	int smallestIndex = 0;
	for(int i=0; i < colors.length; i++) {
		int score = int(abs(red(pixel)-colors[i].getRed()) + abs(green(pixel)-colors[i].getGreen()) + abs(blue(pixel)-colors[i].getBlue()));

		if(score < smallest || smallest == -1) {
			smallest = score;
			smallestIndex = i;
		}
	}

	turtleColors[y*img.width+x] = smallestIndex;

## Run-Length Encoding

The Processing program mentioned above outputs the images in the form of a Java array, so that I can just paste them into the code (the grading server I submit this homework to does not give me file read/write permissions, so I can't just read directly from an image file). Unfortunately, section 4.10 of the JVM Specification (Limitations of the Java Virtual Machine) states that Java methods must take up less than 2^16 bytes. I was easily hitting that limit by statically initializing my image arrays in the source code.
To solve the problem I added code to do [run-length compression](http://en.wikipedia.org/wiki/Run-length_encoding) and decompression. It takes just a few lines to implement in my image converter script and in my drawing code, but it solves the problem and allows me to store/draw large images. It helps that the palette conversion increases the likelihood of long runs of values in the images. Here's what that looks like:

	// compress array into run-length encoded information
	int last = arr[0];
	int len = 1;
	for(int i=0; i < arr.length; i++) {
		int current = arr[i];

		if(current != last) {
			encoded.add(last); encoded.add(len);

			len = 1;
			last = current;
		} else {
			len++;
		}
	}

	// decompress array from run-length information
	for(int i=0; i < compressed.length; i += 2) {
		int val = compressed[i];
		int len = compressed[i+1];
		for(int k=0; k < len; k++) decompressed.add(val);
	}


## The Actual Art

The code drawing some original [artwork of mine](http://hackniac.com/art/board/left.jpg):
![art](http://hackniac.com/images/turtle_soup/turtle_art.gif)

Wish me luck in winning the prize.

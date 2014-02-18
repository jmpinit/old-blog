---
layout: post
title: "<insert title here>"
description: ""
category: "old"
tags: []
---


A person on my hall sent out an email about [this fun little text adventure](http://adventure.cueup.com/) meant to exercise your programming skills. There are three challenges and a bonus. I spent a bit of this morning using it as an opportunity to keep learning Python. For anyone out there looking to cheat, or learn, I've posted my code here.

## Level 1: Roulette

	a = 69069
	c = 1
	m = 2**32

	last = 6
	def next():
		global last
		last = ((a*last+c)%m)
		return last%36

### Solving

	>>> next()
	19L
	>>> next()
	16L
	>>> next()
	29L
	>>> next()
	30L

## Level 2: Closing Mark

{% raw %}
	source = "{{[{{{{}}{{}}}[]}[][{}][({[(({{[][()()]}}{[{{{}}}]}))][()]{[[{((()))({}(())[][])}][]()]}{()[()]}]})][]]}{{}[]}}"

	def push(c):
		global stack
		stack.append(c)
		
	def pop():
		return stack.pop()

	def peek():
		if(len(stack)>0):
			return stack[-1]
		else:
			return None
			
	matches = {'}':'{', ']':'[', ')':'('}
			
	def match():
		global stack
		stack = []
		for i, c in enumerate(source):
			if(c in matches):
				if(peek()==matches[c]):
					g = pop()
				else:
					print "failed at "+str(i)
			else:
				push(c)
{% endraw %}

### Solving

	>>> match()
	failed at 96

## Level 3: Path Finding

	map = [8, 8, 4, 4, 5, 4, 9, 6, 4, 8, 8, 6, 4, 1, 2, 4, 8, 2, 6, 3, 0, 6, 8, 8, 4]

	def cost(x, y):
		return map[y*5+x]

	def go(x, y, total):
		if(x<0 or x>4 or y<0 or y>4):
			return False
		elif(x==4 and y==0 and cost(x, y)+total==35):
			print "success"
			return True
		else:
			new = cost(x, y)+total
			if(new>35):
				return False
			
			if(go(x+1, y, new)):
				print "east"
				return True
			if(go(x-1, y, new)):
				print "west"
				return True
			if(go(x, y+1, new)):
				print "south"
				return True
			if(go(x, y-1, new)):
				print "north"
				return True
				
			return False

### Solving

	>>> go(0, 4, 0)
	success
	east
	north
	north
	west
	east
	east
	north
	east
	east
	north
	True

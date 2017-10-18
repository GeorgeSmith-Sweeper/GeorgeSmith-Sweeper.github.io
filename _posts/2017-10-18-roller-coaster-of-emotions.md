---
layout: post
title: "Roller Coaster of Emotions"
date:  2017-10-17
categories: jekyll update
---

### The Good

Today my mentors and I had our Bi-weekly retrospective, and went over what each of us thought of the previous two weeks of my apprenticeship work.

Although I hadn't been able to implement every requested feature in one of projects, the general vibe was positive and during the retro, and everyone (as far as I know) felt like I had made progress as a developer.

### The Bad

My test suites in my Battle-Ship project have become so large that my laptop slows down as I try to scroll through the file in my terminal! I have a significant amount of duplication in my tests, and the refactoring process is going to take careful thought and concentration before everything is [D.R.Y](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself).

### The Ugly (maybe)

My game board in BattleShip is a 2-d matrix of rows and columns.

![Board]({{ GeorgeSmith-Sweeper.github.io }}/assets/Battle-Ship-Board.png){:class="img-responsive"}

I found a bug today that makes all the rows and columns switch, and makes it extremlly difficult to test the values of specific spots. The strangest part about this bug is this it's intermittant, and difficult to reproduce (the bug may be in my head).

At this point in time I'm not sure what's causing this behavior, and all of my tests are green...

I'm stepping away from the project for a couple of hours before I sink too much more time into bug hunting. Hopefully I'll have some bright ideas later on.






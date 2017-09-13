---
layout: post
title: My First Code Review
date: 2017-09-12
categories: jekyll update
---

Today I received my first code review at 8th Light! I had been waiting on this day since starting a python version of Tic-Tac-Toe back in August, and feverishly adding features to meet simulated client requests.  

For those unfamiliar with what a code review is, this wikipedia definition sums it up quite nicely:

>Code review is systematic examination (sometimes referred to as peer review) of computer source code. It is intended to find mistakes overlooked in software development, improving the overall quality of software.

Code reviews are such a large part of software development, that sites like [Code Review](https://codereview.stackexchange.com/) at stack exchange, exist for the sole purpose of providing programmers with feedback if they're not working with a team of developers.

My code review was an informal process where one of my mentors went though my code, and left detailed comments on sections that needed work (more than I had hoped) and thoughts about how I could revise features.

Below is a snippet of a function that needed to be simplified (for some reason I thought I need five lines of code for this...):

```python
def is_draw(current_state):
  if " " in current_state:
    return False
	else:
	  return True
```

This is what the function looks like now (60% code reduction):

```python
def is_draw(current_state): 
	return " " in current_state
```

The snippet can be reduced to a one-liner, but [PEP8](https://www.python.org/dev/peps/pep-0008/) recommends against compound statements.

There are plenty of complicated changes that can be made it my code, but I doubt I would have given this a second look without an extra set of eyes.

Long live code reviews!

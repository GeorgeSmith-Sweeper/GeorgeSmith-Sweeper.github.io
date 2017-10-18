---
layout: post
title: "Python .copy"
date:  2017-10-17
categories: jekyll update
---

Today while working with a group of lists in Python, I came across the built-in `copy` method. Pythons list method`copy` does exactly what it's name suggests, and returns a shallow copy of the list that it was called on.

Using copy is very declarative, readable, and assumes very little base knowledge from developers who are just getting started with Python.

Here's how it looks in action:

```python
ints = [1, 2, 3]

ints_copy = ints.copy()

print(ints, ints_copy) # [1, 2, 3] [1, 2, 3]

```

Previously when copying an entire list in python I would slice the list from the first index to the last, and assign that to a variable.

```python
ints = [1, 2 ,3]

ints_copy = ints[:]

print(ints, ints_copy) # [1, 2, 3] [1, 2, 3]

```

This works well enough, and saves on a tiny bit of typing, but requires me to remember how slice works (proper syntax, indexing), and hope that anyone looking at my code in the future also has a solid grasp of what I was originally trying to accomplish.

Overall I prefer `copy` and have refactored many of my old slice calls to use it.

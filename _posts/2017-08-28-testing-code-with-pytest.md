---
layout: post
title: "Testing code with pytest"
data: 2017-08-28
categories: jekyll update
---

There are many different suites for working setting up tests for python, but none seem quite as simple to setup, get testing, and move write better code.

The beauty of `pytest` comes from the simplicity of it's test structure. If you want to write a test in pytest, this is what it would look like:

```python
import pytest

def add_one(x):
	return x + 1

def test_answer():
	assert func(3) == 5
```

For comparison, here's how you would write the same test in Unittest:

```python
import unitest

def add_one(x):
	return x + 1

class MyTest(unitest.TestCase):
	def test(self):
		self.assertEqual(add_one(3), 4)
```

After looking at the two examples, pytest clearly requires less code to get up and running, and is more declaritive. Declaritive code often leaves fewer places for bugs to hide, and makes an makes a developers life easier.



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
		self.assertEqual(func(3), 4)
```

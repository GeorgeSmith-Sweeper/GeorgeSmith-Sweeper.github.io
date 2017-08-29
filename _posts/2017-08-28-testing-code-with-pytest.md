---
layout: post
title: "Testing code with pytest"
data: 2017-08-28
categories: jekyll update
---

There are many different testing suites for python, but none seem quite as simple to setup, interact with with, and start writing better code.

The beauty of `pytest` comes from the simplicity of it's test structure. If you want to write a test in pytest, this is what it would look like:

```python
import pytest

def add_one(x):
	return x + 1

def test_answer():
	assert func(3) == 4
```

Here's how you would write the same test in Unittest:

```python
import unitest

def add_one(x):
	return x + 1

class MyTest(unitest.TestCase):
	def test(self):
		self.assertEqual(add_one(3), 4)
```

After looking at the two examples, pytest clearly requires less code to get up and running, and is more declaritive. Declaritive code often leaves fewer places for bugs to hide, and makes a developers life easier.

In the event that you need to have tests automatically run everytime you make a change to your code, you can run `pip install pytest-watch`, and then type `ptw` in your project directory.

As I continue to use Pytest and unlock it's power, I'll update this post to keep everyone abreast of my discoveries! Happy testing! 

[Pytest DOCS](https://docs.pytest.org/en/latest/index.html)

[Pytest-watch](https://pypi.python.org/pypi/pytest-watch)

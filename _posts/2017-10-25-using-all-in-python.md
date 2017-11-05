---
layout: post
comments: true
title: "Python's Built-in all() Method"
date: 2017-10-25
categories: jekyll update
---

Occasionally when I'm working with a lists in Python, I need to make sure that all values inside meet a certain condition, or are a certain value. One of the most basic ways to accomplish this is by looping through each index of the list, and making sure that the value at the current index is equal to the value that I’ve determined.

```python
our_value = 1
our_list = [1, 1, 1]

def are_all_values_1(our_value, our_list):
  for each_value in our_list:
    if each_value is not our_value:
      return False
  return True

are_all_values_1(our_value, our_list) # True
```

While this isn't necessarily a bad approach, it involves nesting a conditional inside of a for-loop, takes up four lines, and creates room for errors to be introduced.

### Using all()

Python gives us the built in method `all()` that can get the job done in one line, is succinct, and leaves very little space for errors. Pythons `all()` method will work on any iterable, and greatly reduces the amount of mental energy needed to set up value checks.

Heres the first example, refactored to use `all()`:

```python
our_value = 1
our_list = [1, 1, 1]

def are_all_values_1(our_value, our_list):
  return all([each_value == our_value for each_value in our_list])

are_all_values_1(our_value, our_list) # True
```


# The Dangers of Using all()

Since `all()` is essentially checking to see if the values in the provided iterable all evaluate to `True` it requires developers to understand how Python views certain values. New developers can easily become confused when doing basic comparisons.

__Checking None__

Lets say that a developer needs to check that all elements in a list are None, and would like to use `all()`.

```python

none_list = [None, None, None]

def are_all_values_none(none_list):
  return all(none_list)

are_all_values_none(none_list) # False
```

In the example above, all values in the `none_list` are clearly equal to `None`, but `all()` still returns `False`.

__Why does this happen?__

We must remember that `all()` is checking to see if every value in the iterable is equal to the [bool](https://docs.python.org/3/library/functions.html#bool) type `True`, and Python treats `None` as neither True, nor False but as a constant with no value.

__How to avoid unexpected returns.__

Lets refactor the previous example to return `True`:

```python
none_list = [None, None, None]

def are_all_values_none(none_list):
  return all(ele == None for ele in none_list)

are_all_values_none(none_list) # True
```

`ele == None` returns the bool type `True` which allows `all()` to correctly check each element in the list.

Developers will run into the same issues when checking iterables containing empty strings, and again with the int `0`. It's wise to get into the habit of using `all()` with a conditional in order to avoid unexpected returns due to type checks.

Remaining aware of the potential gotchas when integrating `all()` into your code will allow you to make the best use of this powerful builtin.

__Enjoy!__

{% include disqus.html %}

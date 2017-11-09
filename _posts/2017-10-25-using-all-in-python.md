---
layout: post
comments: true
title: "Python's Built-in all() Method"
date: 2017-10-25
categories: jekyll update
---
Occasionally when working with iterables, you'll need to make sure that all values inside meet a certain condition, or value. One of the most basic ways to accomplish this is by looping through each index of the iterable, and making sure that the value at the current index is equal to the value that you want.

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

Python gives us the built in method `all` that can get the job done in one line, is succinct, and leaves very little space for errors. Pythons 'all' method will work on any iterable, and greatly reduces the amount of mental energy needed to set up value checks.

Heres the previous example, refactored to use `all`:

```python
our_value = 1
our_list = [1, 1, 1]

def are_all_values_1(our_value, our_list):
  return all([each_value == our_value for each_value in our_list])

are_all_values_1(our_value, our_list) # True
```


# Gotchas when Using all()

Since `all` is essentially checking to see if the values in the provided iterable all evaluate to `True`, it requires developers to understand how Python evaluates particular values. Lets take a look at a couple of gotchas that can occur when dealing with different data types.

__Checking None__

Lets say that a developer needs to check that all elements in a list are `None`, and would like to use `all`.

```python

none_list = [None, None, None]

def are_all_values_none(none_list):
  return all(none_list)

are_all_values_none(none_list) # False
```

In the example above, all values in the `none_list` are clearly equal to `None`, but `all` still returns `False`.

__Why does this happen?__

We must remember that `all` is checking to see if every value in the iterable is equal to the [bool](https://docs.python.org/3/library/functions.html#bool) type `True`, and Python treats `None` as neither True, nor False but as a constant with no value.

Lets refactor the previous example to return `True`:

```python
none_list = [None, None, None]

def are_all_values_none(none_list):
  return all(ele == None for ele in none_list)

are_all_values_none(none_list) # True
```

This time around, `ele == None` returns the bool type `True` which allows `all` to correctly check each element in the list.

__Checking Ints and Strings__

Developers will run into the same issues when checking iterables containing empty strings, and again with the int `0`.

```python
int_and_string = [0,'0', '']

def are_all_values_True(int_and_string):
  return all(int_and_string)

are_all_values_True(int_and_string) # False
```

In Python (and most languages) the int `0` is treated as `False`, and any empty strings also become `False` once evaluated.

### Final Thoughts

While it's tempting to use `all` in every situation that has an iterable, I think that `all` is better used to clean up nested value checks during refactoring.

Remaining aware of the potential gotchas when integrating `all` into your code will allow you to make the best use of this powerful builtin, and create clean, easy to read code.

{% include disqus.html %}

---
layout: post
comments: true
title: "Python's Built-in all() and any() Methods"
date: 2017-10-25
categories: jekyll update
---

Occasionally when I'm working with a lists in Python, I need to make sure that all values inside meet a certain condition, or are a certain value. One of the most basic ways to accomplish this is by looping through each index of the list, and making sure that the value at the current index is equal to the value that I’ve determined.

### Using all()

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

While this isn't necessarily a bad approach, it involves nesting a conditional inside of a for-loop, takes up four lines, and creates room for indent errors to be introduced.

Python gives us a built in method (all) that can get the job done in one line, is succinct, and leaves very little space for errors.

```python
our_value = 1
our_list = [1, 1, 1]

def are_all_values_1(our_value, our_list):
  return all([ele == our_value for ele in our_list])

are_all_values_1(our_value, our_list) # True
```

We can go one step further (although it's a bit extreme) and simply check that all values in the array are equal to each other.

```python
our_list = [1, 1, 1]

def are_all_values_1(our_list):
  return all(our_list)

are_all_values_1(our_list) # True
```

Pythons `all()` method will work on any iterable, and greatly reduces the amount of mental energy needed to set up value checks.

### Using any()


__Major props to you Python!__


{% include disqus.html %}

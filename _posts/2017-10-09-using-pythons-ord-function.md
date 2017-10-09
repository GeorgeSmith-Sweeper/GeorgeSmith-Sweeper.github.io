---
layout: post
title: "Using Pythons Built-in 'ord' & 'chr' Functions"
date: 2017-10-09
categories: jekyll update
---

The project that I'm currently working on requires me to be able to create a list of letters from 'A' to 'J'. I had no idea how to make this happen, so I went on a short trip through stack overflow to get some ideas.

One user said that a list could be generated using the clever bit of code below:

```python
letters = [chr(i) for i in range(ord('A'), ord('J') + 1)]
```

When you run this code in ipython, or any repl, this is the result:

```python
letters = ['A', 'B', 'C', 'D', 'E', 'F', 'G', 'H', 'I', 'J']
```

This works perfectly for my project, but I really want to know what's exactly happening to make this possible.

### How do chr(), and ord() work?

The built-ins chr, and ord, are character converters.

ord() works by converting a passed in string to it's unicode value represented as an integer.

```python
num = ord('A')

print(num) # prints 65
```
chr() works by converting an integer which has been passed in, to it's unicode value represented as a string.

```python
letter = chr(65)

print(letter) # prints 'A'
```

### Magic list explanation

This is what the clever list algorithm looks like after all `chr`, and `ord` functions have been executed (not too crazy anymore). The algorithm will iterate through the range, and `chr(i)` will be converted into a string that occupies the next index in our list!

```python
letters = ['A' for 65 in range(65, 75] # 1st pass
          ['B' for 66 in range(65, 75] # 2nd pass
          ['C' for 67 in range(65, 75] # 3rd pass
                                            # ...
```

Brilliant!

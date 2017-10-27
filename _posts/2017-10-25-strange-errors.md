---
layout: post
title: "Strange Errors"
date: 2017-10-25
categories: jekyll update
---

Sometimes the errors in python make me want to pull my hair out! I've been stuck on the error message
below for the past 2 hours!

```python
TypeError: string indices must be integers
```

This error appeared as I was trying to assign a value to a nested array that had been placed within a dictionary.

```python


values_dict = {'locations': [[1,2]]}
nested_list = [[1, 2, values_dict[0]]]
new_value = 3

for each_location range(nested_list[0][2]['locations']):
  nested_list[each_location][]
```

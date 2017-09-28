---
layout: post
title: "The 'Or' Operator in Python"
date: 2017-09-26
categories: jekyll update
---

Seriously...we're going back to basics with this post. Why? Because I just spent 15 minutes trying to figure out why a simple conditional statement wasn't behaving the way I intended.

### Problem

Lets take a look at a simplified version of the offending code:

```python
user_choice = '4'

if user_choice == '1' or '2' or '3':
  print(user_choice)
else:
  print('invalid choice')
```

What do you think would print to the console when this runs? If you're screaming '4', you're correct, and fully grasp the weird way that the `or` operator works. Lets take a look at why we get a '4' when I'm sure the developer (me) was expecting 'invalid choice'.

When the Python interpreter gets to our conditional, it checks to see what value is being held by `user_choice` ('4').

The interpreter then checks to see if '4' is equal to '1' and stores the result of that evaluation as ```False```.

The interpreter then checks to see if ```False``` ```or '1' or '2'```. Since both '1' and '2' aren't ```None```, meaning that they actually exist, python views them as being ```True```, and short circuits our conditional.

Finally it prints ```4```.


### Solution
Here's the code that allows us to print 'invalid choice' if the user_choice is anything but '1','2',3.

```python
user_choice = '4'

if user_choice == '1' or user_choice == '2' or user_choice == '3':
  print(user_choice)
else:
  print('invalid choice')
```

Once again the interpreter reaches the conditional, it checks to see if user_choice ('4') is equal to '1' and stores the result of that evaluation as ```False```, however it does something different when it reaches the following ```or```.

The interpreter evaluates the entire statement ```user_choice == '2'``` as ```False```, and does the same with ```user_choice == '3'```.

This means that Python is actually viewing our conditional like this after it evaluates each ```or``` separated statement:

```python

if False or False or False:
  print(user_choice)
else:
  print('invalid choice')
```

Because our conditional has no chance of being ```True```, the interpreter moves into the ```else``` block and prints 'invalid choice'.


### Summary
Pairing operators with conditionals can be used to create complex and fine grained logic in certain situations. However when chaining multiple conditions together, it helps to step back and really understand what's happening at each link.

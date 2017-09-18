---
layout: post
title: 'SOLID: Single Responsibility'
date: 2017-09-16
categories: jekyll update
---

This past Thursday while working on the 2nd iteration of my Python Tic-Tac-Toe game, I reached a point where I could no longer add new features without existing code breaking, and causing me to trace error messages throughout many different files.

While it's natural for a couple things to break when adding new features (especially while refactoring), it's troubling to have issues in multiple locations, and in files that look completely unrelated at first glance.

I mentioned these issues to my mentors, and they recommended that I focus on writing code that adhered to SOLID principles from this point on.

SOLID stands for:
+ **S**ingle Responsibility Principle
+ **O**pen/Closed
+ **L**iskov Substitution
+ **I**nterface Segregation
+ **D**ependency Inversion

The rest of this post will focus on defining, and understanding the first part of solid.

### Single Responsibility 
>A class should do the smallest possible useful thing; that is, it should have a single responsibility

This simple statement has shaped an entire way of thinking in OOP and OOD, and is quite a bit harder to achieve than one might think. Let's take a look at a small piece of code for steering a fictitious car:

```python
class SteeringWheel:
  def turn_car(direction):
    # steers the car
	
  def honk(boolean):
    # alert others of danger
```	

While this may look like a perfectly good example of single responsibility, there are a couple of problems which will make this class harder to reuse in the future, and require us to change it's internal structure later.

Steering wheels should only be responsible for modifying the direction that the vehicle is traveling, and shouldn't be in charge of how the horn functions. If we wanted to reuse this class with a race car, we would run into issues because they rarely have horns on their steering wheels. The same is true of vintage cars, and some European models. 

The easiest way to fix the `SteeringWheel` class is to remove the `honk()` method, and place it into it's own class.

```python
class SteeringWheel:
  def turn_car(direction):
    # steers the car

class Horn:
  def honk():
    # alerts others of danger
```

Once this change has been made, `SteeringWheel` only has one responsibility (move the vehicle in the provided direction), and `Horn` is only responsible for honking when called. Although these are very basic examples, and the details for how cars turn, and how horns work are intentionally left out, it is easy to see the purpose of each class.

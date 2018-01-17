---
layout: post
title: "Recursion and the stack"
date:  2018-01-15
comments: true
categories: jekyll update
---

### What is recursion?

Recursion in terms of programming is any program or method that calls itself as part of it's execution.

### What is the stack?

The stack is where all method calls live within a promgram. When a user initalizes a program, the stack is created to create order and store all method calls in the order that they were called. This is a vast over simplification, but the stack will only look at the method on top.

### How does recursion use the stack?

Recursion makes use of the stack by pushing each call to itself onto the stack with a diffeerent value. Each call can be thought of as a level in a building placed one on top of the other until the building is complete. Just like you can't skip a floor when creating a skyscrapper, neither can you skip a call when calling a recursive method.

### How do you use recursion?

Lets take a look at a SIMPLE way to find the factorial of any number (within reason) using recursion. We're going to write a short program called `findFactorial` that takes an integer called `ourNum` and returns it's factorial.

```java

```

### Do you have to use recusion?


### Summary

Recursion has lots of power, but can be dangerous becasue it can blow the stack (run out of memory).
Not all problems need recursion, and some solutions are very hard to follow and debug.
TDD is tough on very large and complex recursive calls.

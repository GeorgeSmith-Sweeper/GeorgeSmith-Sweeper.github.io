---
layout: post
title: "Recursion and the stack"
date:  2018-01-15
comments: true
categories: jekyll update
---

![Stack of pancakes]({{ GeorgeSmith-Sweeper.github.io }}/assets/pancakeStack.jpg){:class="img-responsive"}


### What is the stack?

The stack is where all method calls live within a program. When a user initializes a program, the stack is helps keep order and store all method calls in the sequence that they were called. The stack works by __pushing__ (adding) a method to the top, and __popping__ (removing) a method from the top when it has finished all of its logic and returned a value. Each of these calls in stored in a unique memory location on the stack.

### What is recursion?

Recursion in terms of programming is any program or method that calls itself as part of it's execution. Recursion is a tough thing to reason about because it involves keeping track of the number of times a method has called itself, and what the state of the variables in those calls look like at different levels.

Every recursive call must have a base case (a condition to exit the call), and a recursive case (where some state is modified).

### How does recursion use the stack?

Recursion makes use of the stack by pushing each call to itself onto the stack with a different value. Each call can be thought of as a level in a building placed one on top of the other until the building is complete. Just like you can't skip a floor when creating a skyscraper, neither can you skip a call when calling a recursive method.

This interaction with the stack can have potentially disastrous consequences if the recursion never reaches its base case and continues to pile new calls onto the stack. The stacks finite memory will be consumed by the endless addition of calls, and your system will grind to a halt.

### How do you use recursion?

Lets take a look at a SIMPLE way to find the factorial of any number (within reason) using recursion. We're going to write a short program called `findFactorial` that takes an integer called `ourNum` and returns it's factorial.

```java
public int findFactorial(int ourNum) {
  // base case
  if (ourNum == 1) {
    return ourNum;
  } else {
    return ourNum * findFactorial(ourNum - 1); // recursive case
  }
}
```

Lets take a look at the stack when we run the `findFactorial` method with 3 as `ourNum`.

![Stack Calls]({{ GeorgeSmith-Sweeper.github.io }}/assets/stackCalls.png){:class="img-responsive"}

Each pass through our findFactorial pushes another call to the stack, that cannot be completed until the call above it has completed it's logic, and returned a value. Once the final call (ourNum == 1) is executed we trigger the first part of our conditional and pop that call off the stack. Each subsequent call now has value that it needs to complete it's logic, and give us our final value of `6`.

### Do you have to use recursion?

Certainly not! Anything you can do with recursion, you can also do with loops. Lets look at our findFactorial method with a loop instead.

```java
public int findFactorial(int ourNum) {
    int product = 1;
    while(ourNum > 0) {
      product *= ourNum;
      ourNum--;
    }
    return product;
}
```

The major difference between this version and our recursive implementation is the addition of a product variable that we update on each step of the loop until `ourNum` is zero. These additional variables can add places for bugs to hide if we're not careful (although doubtful with this simple example).

### Summary

* Recursion has lots of power, and can create very elegant and clean methods when compared to using traditional loop.

* Not all problems need recursion, and some large solutions are very hard to follow and debug.

* It can be dangerous because it can blow the stack (run out of memory) if a call never reaches the base case.

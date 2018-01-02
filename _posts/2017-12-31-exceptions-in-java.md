---
layout: post
title: "Handling exceptions in Java"
date:  2017-12-30
comments: true
categories: jekyll update
---

When building software, there's always a chance that your code will be used in some unexpected way, or that some resource that your code relies on will suddenly become unavailable. These events are not "normal" scenario for your code, and are called exceptions.

# So what do we do?

Should we let exceptions run wild in our applications, and cross our fingers that everything will turn out find in the end? __NO!__ We should stand tall, look the exceptions in the eye and __HANDLE__ them.

When we __try__ to use a method or class that has a risk of failing at runtime, we need to be able to __catch__ any errors, and give the application a way to get out of it's current situation.

### What does that look like in code?

Imagine that you've written an application that will fill the gas tank of your car if pulls up to a pump at a gas station. It uses a `fillGasTank` method that makes interacts with a pump instance to get gas.

```java
public void fillGasTank() {
  try {
    Pump pump = new Pump();
    pump.getGas();
    System.out.print("Attempting to fill the tank");
  } catch (OutOfFuelException ex){
    System.out.print("The pump is empty");
  } finally {
    pump.detachHose();
  }
}
```

When the `fillGasTank` method is called, it runs the logic inside the __try__ block first, creates and new pump instance, calls `getGas`, and prints alerts the driver that it's "Attempting to fill the tank".

The prints statement inside the __catch__ block will only run if the `getGas` method throws an `OutOfFuelException` meaning that this pump is completely empty.

The `finally` block will execute whether an exception was thrown or not, and makes sure that the hose detaches from the car.

# Summary

When using "risky" code, always use a try/catch to protect yourself from unexpected behavior. Try/catch blocks aren't meant to protect you from logic errors in your code, but will shield you from many errors that are outside of your control.

{% include disqus.html %}

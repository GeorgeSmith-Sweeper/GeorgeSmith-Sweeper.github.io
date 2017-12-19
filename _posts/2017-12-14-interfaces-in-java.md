---
layout: post
title: "Interfaces in Java"
date:  2017-12-14
comments: true
categories: jekyll update
---

## What is an interface?

What I was first asked this question, my mind immediately went to GUI's, various keyboard and mouse setups, and peripheral accessories. Unfortunately all of my assumptions were incorrect because Java thinks about interfaces in a very different way.

In Java, an interface is a blueprint/contract for how a class will be built, and tells the class exactly what methods it must contain when it is created. Each implementation can be different which allows the interface to remain abstract, and each class that 'implements' it will be considered 'concrete'.

Interfaces have this structure:

```java
public interface Car {
  void start();
  void speedUp();
  void slowDown();
}
```

The methods that are inside of the Car interface are abstract (have no body), which means that any class using this interface must make use of these methods in some way, and can determine their own behavior. The car class is also free to have additional methods (`speedUpRapidly`), as long as it follows the contract laid out by the `Car` interface.

```java
public class Ferrari implements Car {
  void start() {
    engineOn = true;
  }
  void speedUp() {
    speed += 1;
  }

  void slowDown() {
    speed -+ 1;
  }

  void speedUpRapidly() {
    speed += 20;
  }
}

```

When a class implements the Car interface, but leaves out one of the methods stated in the interface, some advanced editors will even warn you that your breaking the contract.

![IntelliJ Error]({{ GeorgeSmith-Sweeper.github.io }}/assets/IntelliJ.png){:class="img-responsive"}


Interfaces help developers to achieve [polymorphism](https://en.wikipedia.org/wiki/Polymorphism_(computer_science)) by allowing a classes to implement an interface from anywhere, and still be able to extend another class.

{% include disqus.html %}

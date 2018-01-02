---
layout: post
title: "Static keyword in Java"
date:  2017-12-29
comments: true
categories: jekyll update
---

# Cryptic key words

Java is a language filled with cryptic keywords. Very few of these keywords actually do what their name implies, which can lead to confusion for new developers. Today we're going to take a quick look at `static`, and try to get a better understanding of what role it plays in the Java ecosystem.

# What does static do?

Static in java means that there is only one instance of something in a class, and it will be shared between all future instances of that class. If you place the static key word in front of a field, and then create a new instance of the class containing that field, the new instance doesn't receive a it's own version of the field, but instead references the original field from the class.

Placing static in front of a method can help to standardize its behavior. Static methods do not make use of instance methods, or instance variables, and will return consistent results because they aren't tied to the state of an instance.

Static methods generally return the same output, if given the same input.

```java
Math.min(1, 2) // ALWAYS returns 1
```


# What does a static variable look like?

Creating a static variable allows you to make a value that is the same for all instances of a class.

```java
class McDonalds {
  private static int storeNumber = 0;

  public McDonalds() {
    storeNumber++;
  }
}
```

In the example above, our `static` int `storeNumber` ensures that any new McDonalds instance of a will come will have a store number, and will update that the shared storeNumber variable when it is created. The static variable is shared between all McDonalds instances. This would allow the McDonalds fast food chain to keep tract of how many stores they had ever opened.

# What is a static method look like?

The keyword static allows a method to run without any instance of the class.
Static methods are called on the class directly, and don't interact with instance variables in any way.

Incorrect way:

```java
class Car {
  static void startEngine() {
    // starts the engine
  }
}

Car jeep = new Car();
jeep.startEngine();
```

Correct way:

```java
class Car {
  static void startEngine() {
    // starts the engine
  }
}

Car.startEngine();
```


# Summary

Using static is as close as you can get to having a global's in Java. You will never have to instantiate a class to use it's methods, and all static fields will be shared.

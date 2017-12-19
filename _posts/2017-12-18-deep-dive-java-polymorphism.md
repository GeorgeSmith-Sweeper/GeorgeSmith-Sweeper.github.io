---
layout: post
title: "Deep dive into Polymorphism"
date:  2017-12-18
comments: true
categories: jekyll update
---

# What is polymorphism?

> The dictionary definition of polymorphism refers to a principle in biology in which an organism or species can have many different forms or stages. This principle can also be applied to object-oriented programming and languages like the Java language. Subclasses of a class can define their own unique behaviors and yet share some of the same functionality of the parent class.

Polymorphism in Java is a massive topic, so it helps to put a bit of structure around the entire concept. In Java there are two different types of polymorphism Static, and Dynamic, and within those categories, there are different achieve it.

# The two types of polymorphism

***

__STATIC__

Static polymorphism is also known as compile time polymorphism, and is mostly achieved through a process called "method over-loading".

Method overloading is demonstrated below:

```java
class GreetingMaker() {

  public String sayHello(String greeting) {
    return greeting;
  }

  public String sayHello(String greeting, String name) {
    return greeting + name;
  }
}

GreetingMaker greeter = new GreetingMaker();
System.out.println(greeter.sayHello("Hello")); // prints Hello
System.out.println(greeter.sayHello("Hello", "George")); // prints Hello George
```

When the compiler gets to our `GreetingMaker` class it sees that there are two methods with the same name (`sayHello`). The compiler then begins to look for what makes the two methods unique and sees that they are called with parameter lists. From this point on, the compiler will only call the first method if there is exactly one argument, and the second method if there are two arguments.

All of this logic happens at compile time which is how this type of polymorphism gets its name.

***

__DYNAMIC__

Dynamic polymorphism can be achieved in Java in a number of ways. Two of the most popular ways are inheritance (demonstrated below), and [interfaces](https://georgesmith-sweeper.github.io/jekyll/update/2017/12/14/interfaces-in-java.html).

Classes in Java inherit the traits of another class through extension. A class that extends another class is considered to be a subclass.

```java
class Animal() {
  public String makeASound() {
    return "Grrrrr"
  }
}

class Donkey extends Animal {
  @Override
  public String makeASound() {
    return "Heee Hawww";
  }
}

Animal tiger = new Animal();
System.out.println(tiger.makeASound()); // "Grrrrr"

Donkey donkey = new Donkey();
System.out.println(donkey.makeASound()); // "Heee Hawww"

```

The Donkey subclass will now have access to the `makeASound` method that was created by the Animal Superclass. The Donkey subclass can also choose to create it's own implementation for an inherited method by adding an `@Override` annotation to the method when the return type, and method signature are the same.

Java determines which version of the `makeASound` method to run based on the object that owns that method. Because Donkey is also an Animal, this is Polymorphic. The JVM is in charge of determining which methods are called after everything has been compiled which is why this type of polymorphism is called runtime.


# Summary

Polymorphism is what makes modern programming and application development possible. It gives developers the ability to create a single object that can behave differently in many unique situations. Without polymorphism developers would spend all day bogged down imagining new objects for every possible situation, and never create anything useful.

{% include disqus.html %}

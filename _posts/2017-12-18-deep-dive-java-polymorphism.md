---
layout: post
title: "Deep dive into Polymorphism"
date:  2017-12-18
comments: true
categories: jekyll update
---

## Polymorphism

> The dictionary definition of polymorphism refers to a principle in biology in which an organism or species can have many different forms or stages. This principle can also be applied to object-oriented programming and languages like the Java language. Subclasses of a class can define their own unique behaviors and yet share some of the same functionality of the parent class.


Polymorphism can be acheived in Java in a number of ways. The main three are inheritance, interfaces, and abstract classes.

* classes extending classes (inheritance)

Classes in Java inherit the traits of another class through extension. A class that extends another class is considered to be a Subclass.

```java
class Animal() {
  public void breath() {}
  public void eat() {}
  public String makeASound() {}
}

class Donkey extends Animal {

  // returns a specific sound for donkeys
  @Override
  public String makeASound() {
    return "Heee Hawww";
  }
}
```

The Donkey class will now have access to the `breath`, `eat`, and `makeASound` methods that were created by the Animal Superclass. The Donkey class can also choose to create it's own implementation for an inherited method by adding an `@Override` anotation to the method when the return type, and method signature are the same.

### Interfaces

Interfaces in Java allows developers to create classes that follow a 'contract' provided by another class, but modify the implementation of those methods in anyway that they see fit. The custom implementations mean that the interface can remain abtract, and each class that 'implements' it will be considered 'concrete'.

```java
public interface Animal() {
  void breath();
  void eat();
  String makeASound();
}

class Donkey implements Animal {

  public void breath() {
    // breaths in donkey style
  }

  public void eat() {
    // eats in a unique way
  }

  public String makeASound() {
    // returns a unique sound
  }
}
```


### Abstract Classes

Abstract classes are very similar to interfaces except that an Abstract class can declare __AND__ implement methods when created.

```java
abstract class Animal() {

  // Default behaviors
  public void breath() {
    // inhale
    // exhale
  };
  public void eat() {
    // chew food
  };

  // abtract method, implemented by its instances
  abtract String makeASound();
}
```


{% include disqus.html %}

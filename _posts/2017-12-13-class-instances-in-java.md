---
layout: post
title: "Class instances in Java"
date:  2017-12-12
comments: true
categories: jekyll update
---

Today is my first full day of working with Java, and I'm starting to wrap my head around class instances, the importance of keeping class fields private while interacting with them through getters and setters, and how constructors and provide an initial state to a new instance.

#### Wrong way

Lets start with a poor example of setting up a class (that will still run).

```java
class Car {
  int price;
  String color;
  int wheels = 4;

  void changeColor(String requestedColor) {
    color = requestedColor;
  }

  void changePrice(int requestedPrice) {
    price = requestedPrice;
  }

  void changeNumberOfWheels(int requestedNumberOfWheels) {
    wheels = requestedNumberOfWheels;
  }
}

Car ferrari = new Car();
ferrari.changeColor("Red");
ferrari.changePrice(1000000);
ferrari.changeNumberOfWheels(6);

System.out.print(ferrari.color);
System.out.print(ferrari.price);
System.out.print(ferrari.wheels);
```

This is a pretty scary example. The class fields are exposed and can be modified by anything that
interacts with the car class. A rouge developer could easily set values on the class with
`Car.color = "whatEverIWant"`, and alter what the original developer had set out to do.
This basically makes the methods on the class useless because anyone can directly modify the class.

This example does not make use of encapsulation, is considered bad practice, and is dangerous in some situations.

#### Right way

This is a much better poor example of setting up a class.

```java
class Car {
  private int price;
  private String color;
  private int wheels;

  // constructor
  public Car() {
    this.price = price;
    this.color = color;
    this.wheels = wheels;
  }

  public int getColor() {
    return this.color;
  }

  public int getPrice() {
    return this.price;
  }

  public int getNumberOfWheels() {
    return this.wheels;
  }
}

Car ferrari = new Car(1000000, "Red", 4);
System.out.print(ferrari.getColor);
System.out.print(ferrari.getPrice);
System.out.print(ferrari.getNumberOfWheels);
```

This example makes use of encapsulation, a constructor, and getter methods.

#### Encapsulation

>Encapsulation is one of the fundamentals of OOP (object-oriented programming). It refers to the bundling of data with the methods that operate on that data. Encapsulation is used to hide the values or state of a structured data object inside a class, preventing unauthorized parties' direct access to them. Publicly accessible methods are generally provided in the class (so-called getters and setters) to access the values, and other client classes call these methods to retrieve and modify the values within the object.

The class fields have been set to `private` which restricts their access to
methods that are within the scope of the class.

```java
  private int price;
  private String color;
  private int wheels;
```


#### Constructor

>A class contains constructors that are invoked to create objects from the class blueprint. Constructor declarations look like method declarations—except that they use the name of the class and have no return type.

```java
  public Car() {
    this.price = price;
    this.color = color;
    this.wheels = wheels;
  }
  //
  //
  //
  //
  //
  //
  //
  //

  Car ferrari = new Car(1000000, "Red", 4);
```

This constructor is responsible for setting the values for the class fields,
and allows a developer to create a `Car` instance with an initial state.

#### Getter Methods

```java
  public int getColor() {
    return this.color;
  }

  public int getPrice() {
    return this.price;
  }

  public int getNumberOfWheels() {
    return this.wheels;
  }
```

The getter methods on the class are only responsible for accessing the values of the private
class fields. They have no way to modify the fields in any way. Using methods in this fashion makes
makes the fields 'read' only.


#### Summary

Following best practices, and making use of encapsulation, constructors, and getter/setter methods,
can prevent many unusual behaviors in creation and use of class instances.

{% include disqus.html %}

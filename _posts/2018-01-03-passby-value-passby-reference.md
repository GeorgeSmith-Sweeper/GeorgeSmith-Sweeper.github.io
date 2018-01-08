---
layout: post
title: "Pass-by-value, Pass-by-reference"
date:  2018-01-03
comments: true
categories: jekyll update
---

### Is Java pass by value, or pass by reference?

Java is pass by value. First we should get a base understanding of what pass by value, and pass by reference are.

__Pass by Value__
>Passing by value constitutes copying of data, where changes to the copied value are not reflected in the original value

__Pass by Reference__
>Passing by reference constitutes the aliasing of data, where changes to the aliased value are reflected in the original value

Cool? Textbook definitions out of the way. Java is pass-by-value when it comes to methods and their arguments. In Java, when you call a method, and provide it with a particular argument, the method is actually working with a copy of what was provided, and not the original.

Let's take a look at an example.

```java
class demo {
  void iTakeNumbers (int aNumber) {
    aNumber = 4;
  }
}

int numOne = 10;
demo.iTakeNumbers(numOne);
```

In our simple example, `iTakeNumbers` modifies the value of it's parameter `aNumber`, by setting that value to be 4. Does the value of numOne change as a result of this method being called?

__NO__. The value of numOne will still be 10 after this method is run because the method received a copy of bits that represent the value of `numOne`.

Things are a bit less clear when passing objects into methods instead of primitives though.

Lets take a look at another example.

```java
public class Main
{
     public static void main(String[] args)
     {
          Foo f = new Foo("f");
          changeReference(f); // It won't change the reference!
          modifyReference(f); // It will change the object that the reference refers to!
     }
     public static void changeReference(Foo a)
     {
          Foo b = new Foo("b");
          a = b;
     }
     public static void modifyReference(Foo c)
     {
          c.setAttribute("c");
     }
}

// source https://stackoverflow.com/questions/7893492/is-java-really-passing-objects-by-value
```

In `changeReference` "Foo a" is created as the method is called, and will point to object "f" that was passed in. When Foo "b" is created, and set to "a", the pointer is moved to reference Foo "b", but the values are not changed.

Something different happens in `modifyReference`. ModifyReference creates and Foo "c" that points to  the object "f" that was passed in (same as `changeReference`), however calling setAttribute on "c" will change the value of "f" because the pointer was not switched by declaring `Foo c  = new Foo("c");` within the method. `setAttribute` will change the attribute on "f" because of the pointer.

## Summary

Java is pass-by-value when passing arguments into methods, and is fairly straight forward when dealing with primitives. Pointers add an extra layer of complexity to the equation when passing in objects, as their values can be modified through their pointer references.

{% include disqus.html %}

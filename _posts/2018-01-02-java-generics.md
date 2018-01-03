---
layout: post
title: "Generics in Java"
date:  2018-01-02
comments: true
categories: jekyll update
---

### What are Generics

Generics in Java are bit of code that is placed in angle brakets (`< >`) during declarations. 
Generics are mainly used to help developers create type-safe collections by allowing types to be parameters,
when defining classes, interfaces, and methods. This allows a developer to reuse the same code with different inputs.

### What does a genertic look like?

```java
Dog greatDane = new Dog();

ArrayList<Dog> allOfOurDogs = new Arraylist<Dog>();

allOfOurDogs.add(greatDane);
```

The line of code above is creating an ArrayList and specifying the type of object that it will hold. This is a pretty big deal, and is the main power of generics. Using generics in this example gives a developer confidence that the objects added to the `allOfOurDogs` ArrayList will always come out as `Dog` references.  

To truly appriciate what that means, you have to first understand that ArrayLists on their own can normally take ANY object, of any type.

```java
Dog greatDane = new Dog();
Cat maineCoon = new Cat();
int ten = 10;
boolean thisIsTrue = true;

ArrayList aBunchOfNonsense = new ArrayList();

aBunchOfNonsense.add(greatDane);
aBunchOfNonsense.add(maineCoon);
aBunchOfNonsense.add(ten);
aBunchOfNonsense.add(boolean);
```

Everything in the example above is perfectly legal in Java, but you might run into some surprises if something unexpected gets added to the ArrayList.

# Summary

# To be Continued

{% include disqus.html %}

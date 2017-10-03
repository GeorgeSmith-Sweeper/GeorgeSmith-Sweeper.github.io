---
layout: post
title: "SOLID: Open / Closed Principle"
date: 2017-10-03
categories: jekyll update
---

This post is a continuation of my SOLID series, and will focus on defining, and understanding the "O" in S.O.L.I.D.

So why should we make sure that our code follows 'Open / Closed'? One compelling reason, is that it makes life easier for future developers who will inherit this project, and want to add functionality. Another reason is that 'Open / Closed' makes code more reusable and easier to reason about.

 Lets start with a quick definition of what Open / Closed is:

>In object-oriented programming, the open/closed principle states "software entities (classes, modules, functions, etc.) should be open for extension, but closed for modification"; that is, such an entity can allow its behavior to be extended without modifying its source code.

Great! I pulled this paragraph straight from Wikipedia, and it left me with more questions than answers...What is mean't by "extension", and how can I change something without modifying it?

### Extension with Modification

Lets imagine that we are developers who have been asked to build an application that runs a giant feeding machine on a farm. This machine is responsible for feeding each animal that the farm has with the correct type of food.

Here's what such an application could look like:

```python
animal_types = {'Dog': 'Dog' , 'Cat': 'Cat', 'Snake': 'Snake', 'Horse': 'Horse'}

class FoodMachine:
  def feed_our_animals(self, animal):
    if animal == 'Dog':
      print('eat meat')
    elif animal == 'Cat':
      print('eat fish')
    elif animal == 'Snake':
      print('eat rats')
    elif animal == 'Horse':
      print('eat hay')
    else:
      print('eat grass')

mealtime = FoodMachine()
mealtime.feed_our_animals(animal_types['Dog'])
mealtime.feed_our_animals(animal_types['Cat'])
```

This set of instructions should work for the animals we currently have on the farm, and would print `eat meat`, and `eat fish`, anytime it's run.

While everything works right now, and the animals, and farmers are happy, what would happens when the farmers suddenly decide that they also want to have a Cow on the farm?!

This violates the 'Open/Closed' because every additional animal would require us to change the code inside of the `FeedOurAnimals` method. Not very extensible.

### Extension without Modification

```python
class Animal():
  def eat(self):
    print('eat grass')

class Dog(Animal):
  def eat(self):
    print('eat meat')

class Cat(Animal):
  def eat(self):
    print('eat fish')

class Snake(Animal):
  def eat(self):
    print('eat rats')

class Horse(Animal):
  def eat(self):
    print('eat hay')

class FoodMachine():
  def feed_our_animals(self, animal):
    animal.eat()


mealtime = FoodMachine()
dog = Dog()
cat = Cat()
mealtime.feed_our_animals(dog)
mealtime.feed_our_animals(cat)
```

This version of our `FoodMachine` allows us to add as many animals as we want without having to change any of the code inside of our `FeedOurAnimals` method, thus making it 'Open' to extension, but 'Closed' to modification. Hooray!







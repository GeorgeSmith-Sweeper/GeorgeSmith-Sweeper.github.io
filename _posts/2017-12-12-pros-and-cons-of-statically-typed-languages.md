---
layout: post
title: "Pros and Cons of Statically typed languages"
date:  2017-12-12
comments: true
categories: jekyll update
---

I have been working with dynamically typed languages for my entire programming career (JavaScript, Python). This week was my first experience with a statically typed language (Java), and I've begun to notice some pros & cons.

### Pros

> Type checking at compile time

One of the major advantages to statically typed languages is type checking at compile time as opposed to runtime. In the example below, the type checker would throw an error because the `getTheString` function is supposed to return a `String`, but returns an `int` instead.

```java
public String getTheString() {
  theString = "10";
  int convertedString = Integer.parseInt(theString);
  return convertedString;
}
```

Dynamically typed languages would allow the `int` to be returned, which could have terrible reprocussions for other methods that depend on that return value.


### Cons

The type errors in Java can be very difficult to understand. Because type errors tend to happen at the point of insertion, a developer can be almost certain that the erroneous code isn't where the error occured.

Most errors will be symantic based instead of logic based, and can eat up precious time that would otherwise be used to build a new feature.

Static languages force you to make design and structural decisions when you might not know what direction your application will go in.

## To Be Continued...

I haven't worked with Java long enough to give a personal analysis of pros and cons at a deeper level. This post will be updated at the end of the week once I get my hands dirty!


{% include disqus.html %}

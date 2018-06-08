---
layout: post
title: "TIL: Using spread with findIndex"
date:  2018-06-07
comments: true
categories: jekyll update
---

![Berry jam being spread on a piece of toast with a knife]({{ GeorgeSmith-Sweeper.github.io }}/assets/jam_spread.jpg){:class="img-responsive"}

Recently I've been working on a project that uses Javascript on the frontend. The frontend consumes information from an api and renders that data.

The information comes in as an array for objects where each object has a unique`id`. One feature request that I've been working to create has been the ability to delete any object, no matter where it lives inside the array.

Back before the release of ES6 and the introduction of `findIndex()`, and the "spread" (`...`) operator, removing a specific item would involve jumping through hoops.

Lets take a look at the ES6 version:

```javascript

````

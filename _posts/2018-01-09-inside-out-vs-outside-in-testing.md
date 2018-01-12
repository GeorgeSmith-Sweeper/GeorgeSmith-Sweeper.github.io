---
layout: post
title: "Inside-out Vs Outside-in testing"
date:  2018-01-09
comments: true
categories: jekyll update
---

[Inside out control terminal]()

### What is inside-out testing?

Inside out testing is a form of testing where the developer focuses on the functionality of individual components, and not how the components interact with each other as a whole.

Finding bugs is more difficult because multiple components must be considered when everything has been put back together.

Helps to create components that follow the single responsibliity principle.

### What is outside in testing?

Focuses on how components interact with each other, and helps to refine the overall design of the application.

Relies heavily on mocks or stubs to represent the flow of information between components. The implementation details of each component is deferred to a later time.

More difficult to acheive in dynamic languages because there are not interface contracts that would tie together the real production implementation with it's equivalent mock.

Helps to
Also known as London style.

### When do you use each?

There is no hard set rule on which style to use.


### Summary

{% include disqus.html %}

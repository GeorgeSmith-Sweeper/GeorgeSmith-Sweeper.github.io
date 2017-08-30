---
layout: post
title: "Starting with TDD"
date: 2017-08-29
categories: jekyll update
---

TDD stands for "Test-Driven Development", and when used correctly can help a developer write code that has fewer bugs, and is more maintainable.

Before beginning my apprenticeship at 8th Light, I wasn't a huge fan of TDD because I thought it was slow tedious work, that stiffled my abilty to be creative in my code.
I used to build entire compontents without tests, and would then spend hours hunting for bugs if anything went wrong. This type of development gave me no hints for debugging when things went wrong, and often forced me to write [Spaghetti code](https://sourcemaking.com/antipatterns/spaghetti-code) to get things working if I was on a deadline.

Here's a quick overview of the steps involved with TDD:

1. Quickly add a test.
2. Run all tests and see the new one fail.
3. Make a little change.
4. Run all tests and see them all succeed.
5. Refactor to remove duplication.

Out of these five steps, the final one is the most time consuming, and occasionally makes me want to [rage-quit](http://gph.is/1jF6r4t) my terminal.
Refactoring should be broken into many tiny steps that build upon each other until your code is optimized and sqeekly clean. In theory refactoring never ends, which means your code can always improve.


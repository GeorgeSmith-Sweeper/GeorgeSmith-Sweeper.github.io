---
layout: post
title: "Unit Testing Randomness"
date:  2017-10-12
categories: jekyll update
---

In my current iteration of BattleShip, I have to create a way for a computer to randomly place ships on a game board in accordance to standard battleship rules.

My first thought was to create a random number generator, that would return an `int` from 0 to 9, and then use that int to access the indices of a 2-d matrix.

I proceeded to write a unit test (TDD) for my random generator, and quickly realized that I wouldn't be able to compare a predetermined int with the int that the generator returned!

### How can you test something that is designed to be random?

[How should I test randomness?](https://softwareengineering.stackexchange.com/questions/147134/how-should-i-test-randomness)

[Unit Testing Random Behavior With Mock Objects](http://jasonjl.me/blog/2014/11/03/testing-the-undeterministic-with-mocking/)

Many articles suggest mocking the random number generator so the test is repeatable, while others say that the only real way to test randomness is statistical distribution tools...

I haven't figured out how to do it yet, but it's encouraging to come across other developers who are having the same issue.


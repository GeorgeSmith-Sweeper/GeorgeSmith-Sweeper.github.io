---
layout: post
title: Continuous integration
date: 2017-09-05
categories: jekyll update
---

Today was my first time working on a project while practicing something called continuous integration.

Here's a quick definition:
>Continuous integration is the practice of routinely integrating code changes into the main branch of a repository, and testing the changes, as early and often as possible. Ideally, developers will integrate their code daily, if not multiple times a day.

Setting up CI for your project can appear daunting at first, but can be maintained easily across many repositories once everything is in place. My tool of choice has been [Travis-CI](travis-ci.org). 

It took me three attempts for my build to pass, and six attempts before I felt like I understood what Travis-CI was doing, and got comfortable with its basic functions.

Red is normally a bad sign:
![Travis Build]({{ GeorgeSmith-Sweeper.github.io }}/assets/Travis-CI.png){:class="img-responsive"}

Travis builds everything in my repository everytime I push new code, runs my tests, and gives me immediate feedback when something is broken. This series of actions allows me to catch bugs before users find them, and gives me a safety net when adding new features.

If you would like a deeper look at what continuous integration is and how you can use it, I found this article very helpful when getting started: [Continuous intergration, explained](https://www.atlassian.com/continuous-delivery/continuous-integration-intro).

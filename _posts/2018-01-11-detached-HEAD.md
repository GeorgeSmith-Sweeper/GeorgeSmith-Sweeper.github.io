---
layout: post
title: "Git detached HEAD"
date:  2018-01-11
comments: true
categories: jekyll update
---
![Floating heads on strings]({{ GeorgeSmith-Sweeper.github.io }}/assets/detachedHead.jpg){:class="img-responsive"}

A couple of days ago I ran into a bit of trouble while working on a branch in a project. I had made incorrects assumptions about the design of a couple of classes in the project, and wanted to go back a couple of commits to a time before creating I had created them.

I asked my mentor if there was a way to go back to a time before my class implementations and he casually responded "git checkout <SHA1 hash of commit>".

I promtly searched for the SHA of the commit that I wanted to return to and ran `git checkout faf6c4c` in my terminal.

I was greeted with this message:

```bash
Note: checking out 'faf6c4c'.

You are now in 'detached HEAD' state...
```

### What is a detached HEAD state?

Git checkout may be your most widly used command when intracting with a project on git. It's most basic usage is to allow you to switch between different project branches.

A detached head is when a commit is checked out instead of a branch and Git has not moved the HEAD pointed to the commit that you are currently on. In laymans terms in mean that the HEAD has become "detached" from the commit that you are viewing.

Being in detached head state can be uncomfortable, becaus any changes, or commits that you make while in that state will remain detached, and float around without a HEAD reference to tie them to the branch.

### Saving commits in a detached HEAD state

If changes are made while in a detached HEAD state, and you'd like to hold to them when you switch to another branch, you can create a new branch with `git checkout -b new_branch_name`, and all of your previous commits will be stored in the newly created branch. Git will move the HEAD pointer to this branch until you choose to switch.

### Summary

Most developers will enter a detached head state at some point in their careers. It can be unnerving at first but git makes it fairly easy to recover from, amd continue working.

{% include disqus.html %}

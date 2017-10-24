---
layout: post
title: "Using 'git stash'"
date: 2017-10-24
categories: jekyll update
---

Today while working on my latest iteration of battleship, I began to feel like I had gone down the wrong path in my design. I had been working on a branch that contained my most recent work, and had modified a large chunk of the code without committing the changes.

The ideal move in this situation is normally to revert the branch back to it's unmodified state, and start again with a clean slate. However, I wanted to hang on some of the code as it was fairly clever, and represented a different approach to the problem.

I began looking for a way to store my changes, create a branch from the clean branch, reapply my changes, and then push the branch, so that I would always have a remote copy of my clever code.

### Enter 'git stash'
`git stash` exists for the exact scenario which I described above. If you run `git stash` on a branch with uncommitted changes, the changes are stored, and `HEAD`is moved to the last commit before the changes.

Once `HEAD` has been moved, it's possible to make a new branch (`git checkout -b <branch-name>`), switch back to your previous branch (`git checkout <previous branch-name>`), and reapply your stored changes (`git stash apply`).

At this point, all the changes have been restored, and can be committed and pushed as normal.

### Summary

It's easier (and smarter) to leave a branch unmodified, and make new branches off of it, than it is to use `git stash`. However if you've already gone too far for that to be an option, then `git stash` is a very handy tool to have.

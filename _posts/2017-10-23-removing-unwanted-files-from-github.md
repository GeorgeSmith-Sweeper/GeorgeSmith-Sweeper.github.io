---
layout: post
comments: true
title: "Removing Files From Github"
date: 2017-10-23
categories: jekyll update
---

Once in a while when working with Github, you may accidentally commit a file (or group of files), that you didn't intend to, and need to remove all traces of it from Github history. This situation often occurs when your `.gitignore` isn't correctly configured to ignore a particular file.

I recently encountered this situation with `pytest` and it's auto generated `.pyc` files, and spent part of this morning figuring out what to do. Here's what I found.

### The Answer

This post on Githubs help articles isn't the most beginner friendly, but is the perfect solution to the problem [Removing sensitive data from a repository](https://help.github.com/articles/removing-sensitive-data-from-a-repository/).

```git filter-branch --force --index-filter \
'git rm --cached --ignore-unmatch PATH-TO-YOUR-FILE-WITH-SENSITIVE-DATA' \
--prune-empty --tag-name-filter cat -- --all
```

This command in particular is very dense, and no explanation is given to how it accomplishes our goal.
One way to understand whats happening, is to realize that the actual command is `git filter-branch` and the rest of the string are simply options.

#### Command
__filter-branch__
>Lets you rewrite Git revision history by rewriting the branches mentioned in the "rev-list options", applying custom filters on each revision. Those filters can modify each tree (e.g. removing a file or running a perl rewrite on all files) or information about each commit.

Basically 'filter branch' will apply every option to the target file, for the entire history of your repository. This is extremely powerful, but disastrous if you modify the wrong file, as you won't be able to run `git revert` as the repository history will have changed.

If you're looking a deeper dive into how `git filter-branch` works, reading the official explanation on [git-scm](https://git-scm.com/docs/git-filter-branch) really helps to clarify the details.

{% include disqus.html %}

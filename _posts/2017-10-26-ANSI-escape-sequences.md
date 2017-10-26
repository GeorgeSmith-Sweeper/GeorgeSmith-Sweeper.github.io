---
layout: post
title: "ANSI Escape Sequences"
comments: true
date: 2017-10-26
categories: jekyll update
---

Today I tackled a very interesting request from my mentors. I had been tasked with changing the colors of print statements in the terminal from the defaults to red based on a conditional.

The conditional logic wasn't the important or interesting part of the problem since it would basically boil down to a `True` or `False` value eventually. The interesting part was trying to find a way to override the default `stdout` colors.

Once I overcame my initial thoughts about this being an impossible to achieve, I starting looking into python modules that could wrap print statements in various colors and display them to the user.

I found two packages that seemed promising ([Termcolor](https://pypi.python.org/pypi/termcolor), and [Colorama](https://pypi.python.org/pypi/colorama)) but they hid their internal workings from me, and forced me to rely on code that I didn't own. The second package ([Colorama](https://pypi.python.org/pypi/colorama)) mentioned something about 'ANSI escape character sequences', and displayed a strange looking code (`'\033[31m'`).

I promptly googled 'ANSI escape character sequences' and found this excellent resource [ascii-table.com](http://ascii-table.com/ansi-escape-sequences.php). Using this as a guide, I was able to decipher the riddle of the terminal, and make some really cool outputs which you can check out [here](https://repl.it/NShK/1).

The key to getting everything working was to change the values of the 'graphics mode'. The 'graphics mode' is in charge of how text is displayed on the screen.

{% include disqus.html %}

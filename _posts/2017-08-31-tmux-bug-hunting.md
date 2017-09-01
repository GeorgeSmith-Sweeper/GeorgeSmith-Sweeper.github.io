---
layout: post
title: Tmux bug hunting
date: 2017-08-29
categories: jekyll update
---

Last night, after a long day of setting up tests and refactoring lines of python, I thought it would be a great idea to jazz up my dev environment with a bit of color, and some syntax highlighting. 

I promptly dove into the docs of [Vim-Plug](https://github.com/junegunn/vim-plug) in order to quickly get up and running with the latest and greatest plugins. Once I felt like a understood how plugins worked, I selected [YouCompleteMe](https://github.com/Valloric/YouCompleteMe) for IDE like autocompletions, [Ultisnips](https://github.com/SirVer/ultisnips) to create useful snippets, and [vim-colors-solarized](https://github.com/altercation/vim-colors-solarized) to better differentiate pieces of code.

Everything was progressing nicely, until I attempted to enable the solarized plugin by adding `set background=dark` and `colorscheme solarized` to my `.vimrc`. The color scheme was applied, but every piece of text on my screen was suddenly surrounded with a black background, as if I had entered visual mode.

Here's an example of what it looked like (not my terminal):

![Before]({{ GeorgeSmith-Sweeper.github.io }}/assets/before_example.png){:class="img-responsive"}

I spent the better part of an hour tearing things down, removing plugins, and rebuilding before a came across this closed issue from 2011: [vim-colors-solarized breaks inside tmux #159](https://github.com/altercation/solarized/issues/159). Apparently there's a `.tmux.conf` file that I knew nothing about that serves the same purpose as my `.vimrc`. 

The magic line that I needed to add was `set -g default-terminal "screen-256color"` which tells tmux to use 256 colors as it's default color format when in the terminal.

Here's what my terminal looked like after adding the line and reloading (my actual terminal):

![After]({{ GeorgeSmith-Sweeper.github.io }}/assets/after_example.png){:class="img-responsive"}

The awful text highlighting was gone!

So what did I learn from this (other than .tmux.conf existence)? __ADD FEATURES ONE AT A TIME!!!__ Not understanding how one plugin interacted with my current setup led to me losing hours of time debugging and undoing prefectly good code.

Never again...I hope.

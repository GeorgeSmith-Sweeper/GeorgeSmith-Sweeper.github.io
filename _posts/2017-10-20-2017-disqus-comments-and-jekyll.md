---
layout: post
title: "Disqus Comments and Jekyll"
date:  2017-10-20
comments: true
categories: jekyll update
---

### Jekyll

Jekyll is a static (the key word being STATIC) site generator that allows anyone to quickly add content to a template, host that content, and display their thoughts to the world.

Out of the box, Jekyll doesn't come with any type of comment integration, which forces a developer to look for a third-party alternative.

### Disqus

Disqus is a 'comment plug-in' that tracks comments in real-time, supports 70 languages, and automatically adapts to the look of your site.

Integrating the dynamic nature of comments into a static site generator like Jekyll, seems like a match made in heaven.

### Trouble

If you've been reading this blog for a while now, you know that it's been a very one sided conversation. I apologize for that, and I've been doing everything I can to get comments enabled on the site (it's just not that easy).

Let's go on a short journey together, so that you can better understand what the hold up has been.

__Poor Writeups__

I know very little about the inner workings of Jekyll or Disqus, so Googling ['adding comments to jekyll'](https://www.google.com/search?q=adding+comments+to+jekyll&oq=adding&aqs=chrome.4.69i57j69i60l3j69i59j69i65.2749j0j7&sourceid=chrome&ie=UTF-8) has been my go to resource.

I've read the top three posts, and they've all presented different ways to accomplish the same thing!

The most useful of the three has been [Keir Whitaker](https://keirwhitaker.com/blog/adding-comments-to-jekyll-blog/), but even with that, I haven't gotten them to work.

__Different Folder Structure__

One thing that I've noticed about each of the comment write ups is that they all mention a _layouts folder which I don't have...

![Folder Structure]({{ GeorgeSmith-Sweeper.github.io }}/assets/Folder-Structure.png){:class="img-responsive"}


### Summary

I'm going to have the commments setup by Monday even if it kills me! I feel like I'm very close to solving this puzzle, and that the answer lies in my _layout! More reading will certainly be required, closly followed by trial and error.

{% include disqus.html %}

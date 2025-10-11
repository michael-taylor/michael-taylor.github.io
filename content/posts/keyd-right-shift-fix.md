---
title: "Fixing \"My Right Shift Acts Like a Left Shift Key\" on Linux"
description: "Fixing a tough-to-trace problem with keyd on Linux"
summary: "Fixing a tough-to-trace problem with keyd on Linux"
date: "2025-10-10"
tags:
  - Linux
---

I've been facing a strange problem lately that was tough to trace down. My <kbd>RIGHT SHIFT</kbd> key was acting like a <kbd>LEFT SHIFT</kbd> key. At first I didn't know that's what was happening. I figured that I was seeing some issues with Wayland on Linux and global keyboard shortcuts. However, I recently got a new keyboard and was using the [Via](https://caniusevia.com/) keyboard mapping software and saw that my <kbd>RIGHT SHIFT</kbd> was sending <kbd>LEFT SHIFT</kbd> signals.

I eventually traced it down to my trusty "easy underscore" keyboard shortcut software, **keyd** _([see my last blog post]({{% relref "easy-snake-case-linux" %}}))_. It turns out that **keyd** combines both <kbd>SHIFT</kbd> key signals into <kbd>LEFT SHIFT</kbd>s.

Thankfully, there's an easy fix if you can live with only using <kbd><kbd>LEFT SHIFT</kbd>+<kbd>SPACE</kbd></kbd> for your underscores. Add `rightshift = rightshift` to your **keyd** config. My config looks like this now:

```
[ids]
*

[main]
rightshift = rightshift

[shift]
space = S-minus
```

I hope this can help someone, because this was really confusing for some time for me.

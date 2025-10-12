---
title: "Making Snake Case More Convenient on Linux"
description: "This one's for you C, C++, and Python programmers on Linux"
summary: "Use Shift+Space to quickly type underscores on Linux"
date: "2025-09-21"
tags:
  - Python
  - C
  - C++
  - Linux
  - Developer Tips
---

> [!WARNING]
> Update: **keyd** introduces a suprising behavior with <kbd>SHIFT</kbd> keys. See [this post]({{% relref "keyd-right-shift-fix" %}}) for a fix.

> [!NOTE]
> If you are on Windows, see this [post]({{% relref "easy-snake-case-windows" %}}) instead.

In my [last post]({{% relref "easy-snake-case-windows" %}}) (almost *two years* ago, wow), I showed how you can more easily type '_' characters in Windows using the <kbd><kbd>SHIFT</kbd>+<kbd>SPACE</kbd></kbd> key combination. Well, it's just as easy in Linux thanks to [keyd](https://github.com/rvaiya/keyd) curtesy of [rvaiya](https://github.com/rvaiya).

First, install **keyd** as shown on its Github link above. For recent releases of Debian and Ubuntu, it now exists in the standard APT repositories, so installation is as easy as `sudo apt install keyd`. :partying_face:

You'll need to add your user to the `keyd` group to enable **keyd** functionality for your user. Do this by running `sudo usermod -aG keyd {username}`.

Finally, add a **keyd** config file to setup the <kbd><kbd>SHIFT</kbd>+<kbd>SPACE</kbd></kbd> as '_' shortcut. Put the following in the file */etc/keyd/default.conf*.

```
[ids]
*

[shift]
space = S-minus
```

You may also need to enable and start the **keyd** service if the installation didn't do that for you. Run the following commands to do that.

* `sudo systemctl enable keyd`
* `sudo systemctl start keyd`

Because your user needed to be added to the `keyd` group, you'll need to log out and log back in to see the effect.


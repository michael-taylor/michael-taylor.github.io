---
title: "Making Snake Case More Convenient"
description: "This one's for you C, C++, and Python programmers"
date: "2023-08-26"
tags:
  - Python
  - C
  - C++
  - Windows
  - Developer Tips
---

One thing that I've always hated about snake_case naming style is that I've always found typing an underscore (_) to be an awkward keystroke. The best thing that I've done to make snake_case typing easier is to use [AutoHotkey](https://www.autohotkey.com/) to create a hotkey to insert an underscore when typing Shift-Space. Here is the AutoHotkey script:

```autohotkey
; Make typing the underscore '_' easier for snake_case_names while programming (now Shift+SpaceBar)
+space::_
```

After some practice, using Shift-Space to insert an underscore becomes natural.

One minor issue is that I sometimes accidentally type an underscore when I type a capital letter before a space by leaving the shift key down a bit too long. This can be worked around by making the hotkey above only active when certain programming applications (Visual Studio Code, Vim, etc.) have focus.

Here is an example that makes the hotkey active only if Visual Studio Code or Notepad has focus:

```autohotkey
#HotIf WinActive("ahk_exe Code.exe") or WinActive("ahk_class Notepad")
+space::_
```

I hope this tip is as valuable to others as it has been for me.

---
title: "Theme generator for Automation Studio"
summary: "Generate theme configs for B&R's Automation Studio IDE"
date: "2025-12-03"
tags:
  - Automation Studio
  - Windows
---

Manually configuring the editor theme of B&R's Automation Studio can be tedious. So, I've created a JavaScript app to generate the editor theme configuration file from some common predefined editor themes. This can be very handy if you prefer dark mode UIs.

Some warnings:

* The utility attempts to theme all the editors from the single theme definition, but I personally mostly use the C editor, so others may not look the best.
* The utility attempts to give "Monitor Mode" a red shift of the editor background color. This doesn't always look good, but you can override it.
* This utility was mostly an excuse for me to learn JavaScript, so it may be buggy. File bug reports at the Github repo here: https://github.com/michael-taylor/as-themer

Anyway, you can try it out here: https://mrt.dev/as-themer

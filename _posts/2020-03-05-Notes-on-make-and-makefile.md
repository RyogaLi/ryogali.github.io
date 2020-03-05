---
layout: post
title:  "Introduction on GNU make (for Python3)"
tags: [Coding]
---

An introduction of make and makefile that I use to make my first makefile. These notes are mainly from the GNU website (https://www.gnu.org/software/make/manual/)

> Make is used to specify dependencies between components in your code. It will compile components in the order required to satisfy dependencies. An important feature is that when a project is recompiled after a few changes, it will recompile only the files which are changed, and any components that are dependent on it.

1. How to write a makefile from scratch?

1.a Rules in makefile

Here is a example of a rule in makefile took from the GNU manual. The `target` often means the executable or object files generated. It can also be the name of an action to carry out.
```
target … : prerequisites …
        recipe
        …
        …
```


1.a The `.PHONY` rule

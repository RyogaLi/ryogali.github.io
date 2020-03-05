---
layout: post
title:  "Introduction to GNU make (for Python3)"
tags: [Coding]
---

An introduction of make and makefile that I use to make my first makefile. These notes are mainly from the GNU website (https://www.gnu.org/software/make/manual/)

> Make is used to specify dependencies between components in your code. It will compile components in the order required to satisfy dependencies. An important feature is that when a project is recompiled after a few changes, it will recompile only the files which are changed, and any components that are dependent on it.

#### How to write a makefile from scratch? ####

1. **Rules in makefile**

Here is an example of a rule in makefile took from the GNU manual. The `target` often means the executable or object files generated. It can also be the name of an action to carry out. `prerequisite` - input files that are used to make the target. `recipe` - the action that make will carry out.
```
target: prerequisites …
  recipe
  …
  …
```
A `rule` is used to tell how and when to remake certain files or executables.

For example, in this case the executable file `edit` depends on eight object files. Then each of the `.o` file depends on other C source and header files.

The rule `clean` does not have any prerequisites and it will not be run by make. You can call `make clean` to execute the recipe.
```
edit : main.o kbd.o command.o display.o \
  insert.o search.o files.o utils.o
    cc -o edit main.o kbd.o command.o display.o \
      insert.o search.o files.o utils.o

main.o : main.c defs.h
        cc -c main.c
kbd.o : kbd.c defs.h command.h
        cc -c kbd.c
command.o : command.c defs.h command.h
        cc -c command.c
display.o : display.c defs.h buffer.h
        cc -c display.c
insert.o : insert.c defs.h buffer.h
        cc -c insert.c
search.o : search.c defs.h buffer.h
        cc -c search.c
files.o : files.c defs.h buffer.h command.h
        cc -c files.c
utils.o : utils.c defs.h
        cc -c utils.c
clean :
        rm edit main.o kbd.o command.o display.o \
           insert.o search.o files.o utils.o
```
When we run `make`, it will start with the first rule in `makefile` and go through each rule to update the files. It will not do anything to the files listed in prerequisites if the file does not depend on anything else. But it does update the target when the prerequisites changed.

2. **Define variables in makefile**

We can define variables in makefile to make it look clean. In the example above, we can define the variable `objects` which refers to the 8 files we use to make `edit`

```
objects = main.o kbd.o command.o display.o \
          insert.o search.o files.o utils.o
```

3. **Make can deduce the recipe**

Sometimes we don't have to tell make what to do exactly in the recipes. For example, it will use `cc -c main.c -o main.o` to compile `main.c` and `main.o`. And we can simplify the makefile into:

```
objects = main.o kbd.o command.o display.o \
          insert.o search.o files.o utils.o

edit : $(objects)
        cc -o edit $(objects)

main.o : defs.h
kbd.o : defs.h command.h
command.o : defs.h command.h
display.o : defs.h buffer.h
insert.o : defs.h buffer.h
search.o : defs.h buffer.h
files.o : defs.h buffer.h command.h
utils.o : defs.h

.PHONY : clean
clean :
        rm edit $(objects)
```

4. **PHONY target**

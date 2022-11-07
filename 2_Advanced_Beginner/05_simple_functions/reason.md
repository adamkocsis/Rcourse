---
parent: "Simple functions"
layout: material 
nav_order: 1
title: Reason
topic: reason_of_functions 
level: "2"
grand_parent: "Level 2 - Advanced Beginner"
---

# Reason for writing functions

Computer functions are like the verbs of proramming. All instructions that we give to the computer are functions. 

As you have seen earlier from nesting of blocks, instructions that we give to the computer can be become quite complex. However, in this complexity we can find logical entities - sets of instructions that we can call to do **One thing**.


# How do custom functions work? 

The idea for custom made functions is that you separate the listing and coding of a set of instructions from the actual execution: you first write done what you want the computer to do in a general way (*function definition*) and then you instruct the computer to execute the instructions (*the function call*).

# What do functions do?

Functions usually either **return a value** or they have some **side effects** - meaning that the state of the programming enviroment changes (e.g. something is printed out or an object changes). 

## Return values

This is a case of return value:

```R
sin(0)
```
```
[1] 0
```

Since the return value is not assigned to a variable, it is redirected to the console, and `show()` is invoked on it. If you assign the return value to a variable, the contents are not displayed:

```R
a <- sin(0)
```

## Side effects

Some functions do not return any values or objects, they just execute other calculations, which do other changes. These include (among many-many):
- plotting
- file manipulation
- printing to the console
- **implement changes to existing objects**. 

This last one is of particular importance, especially if you consider other languages, and when performance key. We use such functions to change options, configure packages and many more.



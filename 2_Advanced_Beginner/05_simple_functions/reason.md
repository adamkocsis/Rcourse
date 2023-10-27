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

Computer functions are the verbs in the language of proramming. All instructions that we give to to a computer are functions. 

As you have seen earlier from nesting of blocks, instructions that we give to the computer can be become quite complex. However, in this complexity we can find logical entities - sets of instructions that we can call one **One thing**.


# How do custom functions work? 

The idea for custom made functions is that you separate the definition (list and coding of small instructions) from the actual execution: you 1) first write done what you want the computer to do in a general way (function's **definition**) and then 2) you instruct the computer to execute the instructions (the **call** to a function).

# What do functions do?

Functions usually either a) **return a value** or b) they have some **side effects** - the latter meaning that the state of the programming enviroment changes (e.g. something is printed out or an object changes). 

## a) Return values

This is a case of return value:

```R
sin(0)
```
```
[1] 0
```

Since the return value is not assigned to a variable, it is redirected to the console. Actually, another function `show()` is called to display it (every time when you write a variable's name into the console to see its value/contents, R does this for you). If you assign the return value to a variable, the contents are not displayed:

```R
a <- sin(0)
```

## b) Side effects

Some functions do not return any values or objects, they just execute calculations, which do other changes. These include (among many-many):
- plotting
- file manipulation
- printing to the console
- **implement changes to existing objects**. 

This last one is of particular importance, especially if you consider other languages (and when performance is key). In R we use such functions to change options, configure packages for example.



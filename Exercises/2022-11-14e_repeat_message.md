---
layout: exercise 
nav_order: 1
title: Repeat message n times
id: 2022-11-14e_repeat_message
parent: Exercise registry
---

## Instructions

#### Part 1

Write a bit of code that prints `My awesome message` to the console as many times as you want (`n`)!

#### Part 2

|--------------|------------------------------------------------------------|
| name:        | `RepMessage()`                                             |
| argument(s): | `x` `(character)`: the message                             |
|              | `n` `numeric`: the number of times the message is repeated |
| return:      | -                                                          |


#### Part 3

Test your new function with the following calls:

```R
RepMessage(x="Coolness", n=5) # should repeat 5 times
RepMessage(x="Nope!", n=0) # should not print anything
```

Think of cases when thing are really wrong! How should we handle those?


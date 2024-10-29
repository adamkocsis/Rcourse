---
layout: exercise 
nav_order: 1
title: Type dependent feedback
id: 2022-11-09b_type_dependent_feedback
parent: Exercise registry
---

## Instructions

#### Part 1

Use the `is.<type>` family of functions to express what the following bit of code is doing in a different way (i.e. you must not use `typeof()`!):

```R
# our input
x <- 12

# feedback
if(typeof(x)=="logical")  feedback <- "Good!"
if(typeof(x)=="double")  feedback <- "Good!"
if(typeof(x)=="integer")  feedback <- "Good!"
if(typeof(x)=="character")  feedback <- "Bad!"
if(typeof(x)=="complex")  feedback <- "Bad!"
message(feedback)
```

Check your code with switching known types for `x`!


#### Part 2

Use the logical operator `|` (or) to simplify the code! 

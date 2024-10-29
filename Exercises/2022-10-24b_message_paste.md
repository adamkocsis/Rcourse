---
layout: exercise 
nav_order: 1
title: Messaging pasted values 
id: 2022-10-24b_message_paste
parent: Exercise registry
---


## Instructions

Modify the following code to display your name and age as a console message (with `message`)!

* * *

### Part 1

Change `name` and `age` to display your name and age. 

```r
name <- ""
age <- 0
input <- paste("I am", name, "and I am", age, "years old.")
message(input)
```

* * *

### Part 2

Replace `paste()` with `paste0()`, and adjust the arguments in it so you can add the comma after your name!


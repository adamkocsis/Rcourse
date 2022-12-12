---
layout: exercise 
nav_order: 1
title: Paraphrasing a sequence
id: 2022-12-12c_sequence_para 
parent: Exercise registry
---

# Paraphrasing sequences

Take a look at this clunky bit of code:

```R
start <- 4
end <- -9 
n <- end-start
a <- start
count <- 1
while(count <=abs(n)){
    a <- c(a, start- count)
    count <- count +1 
}
```	

### Part 1

Use the 1`seq()` function to recreate the `a` vector!

### Part 2

Use the colon operator (`:`) to recreate the `a` vector!

 



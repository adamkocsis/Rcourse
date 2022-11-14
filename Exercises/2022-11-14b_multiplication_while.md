---
layout: exercise 
nav_order: 1
title: Multiplication with a <tt>while()</tt> loop
id: 2022-11-14b_multiplication_while
parent: Exercise registry
---

## Instructions

Here is this simple R code:

```R
a <- 5
b <- 4
result <- a * b
```

Assuming that we do not know how to multiply with `*`, we can still calculate `result` with addition and iteration
(multiplication is achieved with the iteration of addition):

```
3 * 4 = 3 + 3 + 3 + 3
```

Write a `while()` loop to calculate `result` above, without using the the multiplication operator `*`!



*Note: this will be insanely ineffective and we never do this in actual applications (multiplications are optimized at the hardware level, so this is a very slow solution). Nevertheless, this is a good exercise to test your understanding of the `while()` loops!

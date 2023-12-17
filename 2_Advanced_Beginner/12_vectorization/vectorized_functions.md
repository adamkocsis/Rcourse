---
parent: Vectorization 
layout: material 
nav_order: 2
title: "Vectorized functions" 
topic: "vetorized_functions"
level: "2"
grand_parent: "Level 2 - Advanced Beginner"
---

We have seen this example to subset multiple values from a vector:

```R 
# values to subset
numbers <- c(-4, 6, -3, 5, -2, 4, -1, 3)

# subscript indices
indices <- c(2, 4, 6, 8)

# The subsetting
numbers[indices]
```
```
[1] 6 5 4 3
```

# The idea of vectorization

This solution is achieved via the concept of [array programming](https://en.wikipedia.org/wiki/Array_programming), or *vectorization* (as it is referred to in R). *Vectorization* allows us the simplification of an expression of repeated operations (such as the subsetting above) and makes it easy express them without explicitly using iterations such as `for` and `while` loops. This is possible because of the homogeneity of vectors: we can safely assume that if a calculation can be done with one element of the vector, we can do it with all of them - and just automatically repeat every operation that you can do with one value, with all elements of a vector. 

This simplification is so profoud that we typically do not even think about concepts of repetition when we use these instructions. You either do one thing with the **whole** vector, org just rather think about objects that morph into each other. 

Most basic functions that work with single values are vectorized out of the box. For instance consider the `abs()` function that calculates the absolute value of a value. 


```R
a <- abs(-3.5)
a
```
```
3.5
```

Or with a positive value:


```R
b<- abs(7)
b
```
```
7
```

If we could do this only one-by-one, then repeating the process on an arbitrary vector of values, such as this:

```R
vals <- c(-3, 5, 1, 1, -7, 9, -1.7, 4)
```

Requires iteration:

```R
# store the results somewhere else
res <- rep(NA, length(vals))

# iterate for every value of vals
for(i in 1:length(vals)) res[i] <- abs(vals[i])

# the result (floating point numbers)
res
```
```
[1] 3.0 5.0 1.0 1.0 7.0 9.0 1.7 4.0
```

Vectorization allows us the implementation of this simple, perfectly equivalent solution

```R
abs(vals)
```
```
[1] 3.0 5.0 1.0 1.0 7.0 9.0 1.7 4.0
```

All mathematical functions are vectorized and so are the operations, such as the logical NOT (`!`), which will invert every logical value i n a vector:

```R
logVec <- c(TRUE, FALSE, TRUE)
!logVec
```
```
[1] FALSE  TRUE FALSE
```


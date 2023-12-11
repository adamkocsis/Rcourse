---
layout: exercise 
nav_order: 1
title: Distance matrix between points 
id: 2023-12-11_distance-matrix
parent: Exercise registry
---


Consider the following points

```R
points <- matrix(c(
	1,4,
	2,2,
	3,1,
	0, -1
), ncol=2, byrow=TRUE)
rownames(points) <- letters[1:4]
colnames(points) <- c("x", "y")
points
```
```
  x  y
a 1  4
b 2  2
c 3  1
d 0 -1
```

![]({{site.url}}{{site.baseurl}}/images/point_exercise.png)

# Instructions

Calculate a distance matrix between these points! Use the function `distance()` that was defined [here]({{site.url}}{{site.baseurl}}/2_Advanced_Beginner/10_matrices_and_arrays/using_matrices.html). Instead of relying on manual repetition of instructions, use iteration (`for` loops). The matrix should have exactly 16 values, with a `dim` attribute of `c(4,4)`.

> Hint: the elegant solution to the problem involves two for loops, one nested in the other! 

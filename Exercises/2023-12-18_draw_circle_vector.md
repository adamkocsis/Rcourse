---
layout: exercise 
nav_order: 1
title: Drawing a circle - take 2
id: 2023-12-18_draw_circle_vector
parent: Exercise registry
---

## Instructions

![img]({{site.url}}{{site.baseurl}}/images/circle.png)

Write a function to repeat the plotting above based on the following parameters (similar to this earlier exercise: [Drawing a circle](https://adamkocsis.github.io/rkheion/Exercises/2022-11-21b_draw_circle.html)).  

|-----------|--------------------------------------------------------------|
| name      | `Circle()`                                                   |
| arguments | `x` : x coordinate of origin                                 |
|           | `y` : y coordinate of origin                                 |
|           | `r` : radius                                                 |
|           | `by` : the angle step size in degrees                        |
|           | `plot` : logical, if TRUE, then the circle should be plotted |
| return    | A 2D `matrix` with `x` and `y` coordinates                   |
	

**Try to implement this exercise using vectorization principles only, without using either `for` or `while` loops!**

Important: do not draw the basic plot with the function, assume that people will call to it, before calling to `Circle()`. The plot above should be redrawable with these instructions:

```R
plot(0,0)
circle <- Circle(x=0, y=0, r=1, by=5, plot=TRUE)
```


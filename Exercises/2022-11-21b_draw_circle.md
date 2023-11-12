---
layout: exercise 
nav_order: 1
title: Drawing a circle
id: 2022-11-21b_draw_circle
parent: Exercise registry
---

## Instructions

#### Part 1

Use a `while()` loop and the trigonometric functions `sin()` and `cos()` to draw a radius=1 circle around the origin (0,0) with `points()`, the points are exactly 5 degrees apart! Remember that the trigonometric functions accept radians as input! The result should look something like this:

![img]({{site.url}}{{site.baseurl}}/images/circle.png)


#### Part 2

Write a function to repeat the plotting above based on the following parameters. 

|-----------|-------------------------------------|
| name      | `DrawCircle()`                        |
| arguments | `x` : x coordinate of origin          |
|           | `y` : y coordinate of origin          |
|           | `r` : radius                          |
|           | `by` : the angle step size in degrees |
| return    | -                                   |

Important: do not draw the basic plot with the function, assume that people will call to it, before calling to `DrawCircle()`. The plot above should be redrawable with these instructions:

```R
plot(0,0)
DrawCircle(x=0, y=0, r=1, by=5)
```


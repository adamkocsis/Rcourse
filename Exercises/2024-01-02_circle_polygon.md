---
layout: exercise 
nav_order: 1
title: Drawing a circle - take 3 (polygon)
id: 2024-01-02_circle_polygon
parent: Exercise registry
---

## Instructions

![img]({{site.url}}{{site.baseurl}}/images/circle_polygon.png)

Write a function to repeat the plotting of our earlier circle: [Drawing a circle](https://adamkocsis.github.io/rkheion/Exercises/2022-11-21b_draw_circle.html).  

|-----------|---------------------------------------------------------------|
| name      | `Circle()`                                                    |
| arguments | `x=0` : x coordinate of origin                                |
|           | `y=0` : y coordinate of origin                                |
|           | `r=1` : radius                                                |
|           | `by=5` : the angle step size in degrees                       |
|           | `col=1` : the fill color of the circle polygon                |
|           | `border=1` : the circle polygon's border color                |
|           | `lty=1` : the circle polygon's border type                    |
|           | `lwd=1` : the circle polygon's border width                   |
| return    | Either nothing, or a 2D `matrix` with `x` and `y` coordinates |
	
- Similar to the earlier version ([Drawing a circle](https://adamkocsis.github.io/rkheion/Exercises/2023-12-18_draw_circle_vector.html)), try to implement this exercise using vectorization principles only, without using either `for` or `while` loops!

- Instead of using the `return()` function to indicate the return value from the function, try out `invisible()`, instead! 

**Important**: do not draw the basic plot with the function, assume that people will call to it, before calling to `Circle()`. The plot above should be redrawable with these instructions:

```R
plot(0,0)
Circle(x=0, y=0, r=1, by=5, col="#4466FF44")
```


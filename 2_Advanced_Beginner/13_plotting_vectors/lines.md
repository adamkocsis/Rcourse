---
parent: Vectorized plotting 
layout: material 
nav_order: 3
title: "Lines" 
topic: "vectorized_lines"
level: "2"
grand_parent: "Level 2 - Advanced Beginner"
---


## Drawing lines

With vectorization we can draw multiple points at the same time by providing the coordinates to the points as vectors. 


```R
# empty plot
plot(NULL, xlim=c(-1, 1), ylim=c(-1,1))

# the coordinates
xVect2 <- seq(-1, 1, 0.2)
yVect2 <- c(0.4, 0.9, 0, -0.6, -0.5, 0.1, 0.3, -0.7, 0.5, -0.9, 0.6) 
points(x=xVect2, y=yVect2, pch=16)
```

![]({{site.url}}{{site.baseurl}}/images/vector_line_points.png)

Besides saving the time and effort by not having to use iteration explicitly, this kind of syntax allows us to define how the points should be connected. This is exactly what the `lines()` function does. Its syntax is almost exactly the same as that of `points()`:


```R
# empty plot
plot(NULL, xlim=c(-1, 1), ylim=c(-1,1))

# the coordinates
lines(x=xVect2, y=yVect2)
```

![]({{site.url}}{{site.baseurl}}/images/vector_lines.png)

You have the option to modify the `type` of the line plot. This describes the relationship between the point coordinates and the actual lines. See `?lines` and search for `type` argument, which will direct to possible argumets for the `type`.

Similar to `segments()`, `abline()` and `rect()` you can set the `lty` argument for the line style (solid, dashed, dotted), and the `lwd` argument for the with of the line.

```R
# empty plot
plot(NULL, xlim=c(-1, 1), ylim=c(-1,1))

# the coordinates
lines(x=xVect2, y=yVect2, type="o", lty=3, col="blue")
```

![]({{site.url}}{{site.baseurl}}/images/vector_lines_arg.png)

> Similar to `points()` the `lines()` function is extremely important in practical data analysis. It is frequently used to visualize series of points such as time series.


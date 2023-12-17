---
parent: Vectorized plotting 
layout: material 
nav_order: 1
title: "Vectorized points" 
topic: "vetorized_points"
level: "2"
grand_parent: "Level 2 - Advanced Beginner"
---



## Drawing multiple points

Plotting is in practice also uses vectorization, rather than drawing individual points and segments.

Let' consider the simple case of drawing points. Plotting a single point requires an x and a y coordinate:

```R
plot(NULL, xlim=c(-1, 1), ylim=c(-1,1))
points(x=0.5, y=0.5, pch=3)
```

![]({{site.url}}{{site.baseurl}}/images/vector_point.png)

if we want to plot multiple points, we can use vectors as arguments as input. 

```R
# empty plot
plot(NULL, xlim=c(-1, 1), ylim=c(-1,1))

# the coordinates
xVect <- seq(-1, 1, 0.1)
yVect <- seq(-0.3, 0.5, length.out=length(xVect))
points(x=xVect, y=yVect, pch=3)
```

![]({{site.url}}{{site.baseurl}}/images/vector_points.png)


However, `points()` is defined so that it will not recycle coordinates - you have to provide the same number of values for the `x` and `y` arguments, otherwise it will throw a notorious error: 

```R
# will produce an error
points(x=seq(-1, 1, 0.5), y=0.25, pch=3)
```
```
Error in xy.coords(x, y) : 'x' and 'y' lengths differ
```

## Varying point characteristics 

R will recycle values that control the characteristics of the points - their color, size and shape. This is why we can do the drawing of multiple points in the first place. The arguments are recycled (all colors are black, which is the default, and the single value for the `pch` argument is also repeated as many times as many points we have). If you provide vectors for these arguments, R will try to match up every point with one value.

```R
# empty plot
plot(NULL, xlim=c(-1, 1), ylim=c(-1,1))

# every point gets its own size
cexVect <- seq(0.5, 6, length.out=length(xVect))

# vary the symbol - will be repeated following the rules of recycling
pchVect <- c(1, 2, 3,4)
points(x=xVect, y=yVect, pch=pchVect, cex=cexVect, col="red")
```


![]({{site.url}}{{site.baseurl}}/images/vector_points_vary.png)

This example illustrate 3 different ways of using these arguments:

- Color (`col`): a single value is provided, which is repeated to match the number of points. 
- Size (`cex`): one value is provided for every point, exactly as many values as many points.
- Shape (`pch`): A short vector is provided with three symbols. These are repeated following the rules of recycling to match the number of points. (note that in this case, if the number of points is not a multiple of the number of values you provide, you WILL NOT get a warning.




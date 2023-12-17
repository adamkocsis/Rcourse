---
parent: Vectorized plotting 
layout: material 
nav_order: 4
title: "Polygons" 
topic: "vectorized_polygons"
level: "2"
grand_parent: "Level 2 - Advanced Beginner"
---

## Drawing polygons

If we can connect the dots to form shapes, we can also define an area that they encolse. The `polygon()` function wors almost identical to `lines()`, but it also defines an area to be filled, which needs color:


```R
xVect <- seq(-1, 1, 0.2)
yVect <- c(0.1, 0.25, 0.3, 0.45, 0.5, 0.6, 0.55, 0.4, 0.35, 0.2, 0.1) 
# empty plot
plot(NULL, xlim=c(-1, 1), ylim=c(-1,1))

# the coordinates
polygon(x=xVect, y=yVect, col="red")
```


![]({{site.url}}{{site.baseurl}}/images/vector_polygon.png)

The 'polygon' will always be closed automatically, if the first and the last point pairs do not coincide. This basic function can be used to plots shapes in 2D (including actual spatial data). 




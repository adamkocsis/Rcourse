---
parent: Vectorized plotting 
layout: material 
nav_order: 2
title: "Vectorized shapes" 
topic: "vetorized_shapes"
level: "2"
grand_parent: "Level 2 - Advanced Beginner"
---


Unlike `points()`, the functions `segments()`, `abline()`, and `rect()` will let you draw multiple shapes with different-length vectors provided as main arguments.

For instance, a single segment is drawn with this instruction: 

```R
# empty plot
plot(NULL, xlim=c(-10, 10), ylim=c(-10,10))
# segment
segments(x0=-5, y0=-8, x1=7, y1=6)
```

![]({{site.url}}{{site.baseurl}}/images/vector_segment.png)

# Repeating segments

Providing vectors as arguments will draw multiple segments:

```R
# empty plot
plot(NULL, xlim=c(-10, 10), ylim=c(-10,10))
# segment
segments(x0=-5, y0=-8, x1=7, y1=-10:10)
```

![]({{site.url}}{{site.baseurl}}/images/vector_segments.png)

In this case, all values that are shorter than the minimum number of segments that should be drawn (the longest argument vector) will be repeated, so every segment has all four required coordinates.

If more vectors are givenarguments are given, than they will be used. In this case the the 21 lines are drawn with `x0` and `y1` given as vectors. 

```R
# empty plot
plot(NULL, xlim=c(-10, 10), ylim=c(-10,10))
# segment
segments(x0=-10:10, y0=-10, x1=10, y1=-10:10)
```

![]({{site.url}}{{site.baseurl}}/images/vector_segments2.png)

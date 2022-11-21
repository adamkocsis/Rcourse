---
layout: exercise 
nav_order: 1
title: Golden Rectangles
id: 2022-11-21c_golden_rectangles
parent: Exercise registry
---

The following bit of code plots the [golden rectangles](https://en.wikipedia.org/wiki/Golden_rectangle) in [golden spiral](https://en.wikipedia.org/wiki/Golden_spiral) patterns which is frequently used in art, and is often found in natural phenomena:

```R
# the golden ratio
phi <- (1 + sqrt(5))/2

# starting coordinates
x1 <- 0
x2 <- 1
y1 <- 0
y2 <- 1/phi

# basic plot
plot(0,0, axes=F, xlab="", ylab="", type="n",asp=1, xlim=c(0,1), ylim=c(0,y2))

# base rectange
rect(xleft=x1,xright=x2,ybottom=y1, ytop=y2)

##########################
# Iteration 1
# 1st square
x3 <- x1 + (x2-x1) / phi
rect(xleft=x1, xright=x3, ybottom=y1, ytop=y2)

# 2nd square
y3 <- y1 + (y2-y1) / phi
rect(xleft=x3, xright=x2, ybottom=y1, ytop=y3)

# 3rd square
x4 <- x2 - (x2 - x3) / phi 
rect(xleft=x4, xright=x2, ybottom=y3, ytop=y2)

# 4th square
y4 <- y2 - (y2-y3) / phi 
rect(xleft=x3, xright=x4, ybottom=y4, ytop=y2)

# 5th
x5 <- x3 + (x4-x3) / phi
rect(xleft= x3, xright=x5, ybottom=y3, ytop=y4)

# 6th
y5 <- y3 + (y4-y3) / phi
rect(xleft=x5, xright=x4, ybottom=y3, ytop=y5)

# 7th
x6 <- x4 - (x4-x5) / phi
rect(xleft=x6, xright=x4, ybottom=y5, ytop=y4)

# 8th
y6 <- y4 - (y4-y5) / phi 
rect(xleft=x5, xright=x6, ybottom=y6, ytop=y4)
```

![img]({{site.url}}{{site.baseurl}}/images/golden_rectangle.png)

## Instructions

Explore how you can make this plot more beautiful by setting the parameters of the squares (e.g. adding colors, change line widths)! Explore `?rect`! 

## Bonus

This pattern is **recursive** and plotting code above can actually be iterated relatively easily. Can you make this a proper iteration? 

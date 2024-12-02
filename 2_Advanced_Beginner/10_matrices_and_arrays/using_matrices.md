---
parent: Matrices and arrays 
layout: material 
nav_order: 5
title: "On using matrices"
topic: "using_matrices"
level: "2"
grand_parent: "Level 2 - Advanced Beginner"
---

# Why

Matrices are the first objects, that resemble normal tables, so it might be tempting to use matrices in when we want to represent tabular data. The use of the `matrix` class however is not always justified for this and there are special cases when you would prefer storing data in matrices compared to R's general class to store tabular data: the `data.frame`. Matrices store the data of the same `type` and typically do not discriminate between rows and columns in functionality. 

A good example for this is the so-called contingency table (which can be generated with the `table` function), that registeres the number of times, a particular combination occurs. 

```R
# table of experiences
ex <- matrix(c(
	5 , 0,
	1, 3,
	6 , 2
	), ncol=2, nrow=3,
	byrow=TRUE
)
colnames(ex) <- c("John", "Jane")
rownames(ex) <- c("skydiving", "scubadiving", "basejumping")
ex
```
```
            John Jane
skydiving      5    0
scubadiving    1    3
basejumping    6    2
```

This contingency table of experiences is expressing the same information regardless of the dimensions, whether the names are in the rows or the columns. We might decide to gather more data about either the activities or the people. At this point it is totally unimportant what is in the focus.

# Transposition

We can easily change the dimensions by transposing the matrix. In R this is implemented with the `t()` function:

```R
trEx <- t(ex)
trExt
```
```
	 skydiving scubadiving basejumping
John         5           1           6
Jane         0           3           2
```

The information content of the object did not change. Its structure, has - feel free to compare them with `dim()`, `rownames()`, `colnames()` or plain old `str()` - but not what the values mean, or how the data can be used. This is especially the case, when we have symmetric matrices. 


# Coordinates

Matrices are frequently used when registering coordinates - for example x and y coordinates for plotting, or for registering geographic coordinates, longitude and latitude data.

Consider the following points:

```R
p<- matrix(c(
	1, -1,
	1, 0,
	0, 1
), ncol=2, byrow=TRUE)
rownames(p) <- letters[1:3]
colnames(p) <- c("x", "y")
p
```
```
  x  y
a 1  -1 
b 1  0 
c 0  1
```

This matrix includes three points, which can be easilly visualized with iteration:

```R
# draw an empty plot, with default limits
plot(0,0, col=NA)
# show the points, one-by-one
for(i in 1:nrow(p))
	points(x=p[i,"x"], y=p[i, "y"], pch=16)
```

![]({{site.url}}{{site.baseurl}}/images/points_for_distmat.png)

*This gives you very explicit control on how you visualize the points (but there is an easier way to work with these, which we will use when we discuss vectorization).*

Matrices are ideal for storing such data.

# Distance matrices

A matrix is a typical structure that we use to store values that pertain to an arbitrary combination of two entities, for instance if we want to consider the distances between the points in the example above. These can be represented with segments between the points:


```R
segments(x0=p[1, "x"], y0=p[1, "y"], x1=p[2, "x"], y1=p[2, "y"], col="red", lty=2)
segments(x0=p[2, "x"], y0=p[2, "y"], x1=p[3, "x"], y1=p[3, "y"], col="red", lty=2)
segments(x0=p[1, "x"], y0=p[1, "y"], x1=p[3, "x"], y1=p[3, "y"], col="red", lty=2)
```

![]({{site.url}}{{site.baseurl}}/images/points_for_distmat_segments.png)

The distance matrix would be exactly following structure

```R
vals<- rep(NA, 9)
dim(vals) <- c(3,3)
colnames(vals) <- rownames(p)
rownames(vals) <- rownames(p)
vals
```
```
   a  b  c
a NA NA NA
b NA NA NA
c NA NA NA
```

In this matrix, every value (wihch is missing for now), represents a distance between two points: one's name in the row, the other's name in the column. How do we fill it?

First, we have to figure out the distances between two points. This is easy, the distances between two points is nothing else, but the square root of the coordinate's difference squared. If `x0` and `y0` represent the first point, and `x1` and `y1` represent the second, this can be calculated with :

```R
sqrt((x1-x0)^2 + (y1-y0)^2)
```

This is called Euclidean distance. 

We can easilly make this a function (actually, there is already one in R but let's use our own for fun!):

```R
#' The Euclidean distance between two points
#'
#' @param x0 X coordinate of the first point.
#' @param y0 Y coordinate of the first point.
#' @param x1 X coordinate of the second point.
#' @param y1 Y coordinate of the second point.
#' @return The distance value
distance <- function(x0, x1, y0, y1){
	sqrt((x1-x0)^2 + (y1-y0)^2)
}
```

Manually we do this by doing a pairwise enumeration: we have to go through the values of the matrix, one-by-one. Note that if we want the matrix to be full, we have to calculate the distance between a point and itself!

```R
# the two points to compare
p1 <- "a"; p2 <- "a"
# one distance value
oneVal <- distance(x0=p[p1, "x"], y0=p[p1, "y"], x1=p[p2, "x"], y1=p[p2, "y"])
oneVal
```
```
[1] 0
```

Once a single value is calculated, we can store it in the appropriate place. This is an excellent opportunity to use character subscripts!

```R
vals[p1, p2] <- oneVal
vals
```
```
   a  b  c
a  0 NA NA
b NA NA NA
c NA NA NA
```

Now we just have to repeat the same process for all the combinations...

```R
p1 <- "a"; p2 <- "b"
vals[p1, p2] <- distance(x0=p[p1, "x"], y0=p[p1, "y"], x1=p[p2, "x"], y1=p[p2, "y"])

p1 <- "a"; p2 <- "c"
vals[p1, p2] <- distance(x0=p[p1, "x"], y0=p[p1, "y"], x1=p[p2, "x"], y1=p[p2, "y"])

p1 <- "b"; p2 <- "a"
vals[p1, p2] <- distance(x0=p[p1, "x"], y0=p[p1, "y"], x1=p[p2, "x"], y1=p[p2, "y"])

p1 <- "b"; p2 <- "b"
vals[p1, p2] <- distance(x0=p[p1, "x"], y0=p[p1, "y"], x1=p[p2, "x"], y1=p[p2, "y"])

p1 <- "b"; p2 <- "c"
vals[p1, p2] <- distance(x0=p[p1, "x"], y0=p[p1, "y"], x1=p[p2, "x"], y1=p[p2, "y"])

p1 <- "c"; p2 <- "a"
vals[p1, p2] <- distance(x0=p[p1, "x"], y0=p[p1, "y"], x1=p[p2, "x"], y1=p[p2, "y"])

p1 <- "c"; p2 <- "b"
vals[p1, p2] <- distance(x0=p[p1, "x"], y0=p[p1, "y"], x1=p[p2, "x"], y1=p[p2, "y"])

p1 <- "c"; p2 <- "c"
vals[p1, p2] <- distance(x0=p[p1, "x"], y0=p[p1, "y"], x1=p[p2, "x"], y1=p[p2, "y"])
vals
```
```
         a        b        c
a 0.000000 1.000000 2.236068
b 1.000000 0.000000 1.414214
c 2.236068 1.414214 0.000000
```

Distance matrices always have `0`s in their diagonal because the distance between the entities and themselves are always 0. Also note that this is a symmterical matrix: if you transpose it, you will get itself back:

```R
t(vals)
```
```
         a        b        c
a 0.000000 1.000000 2.236068
b 1.000000 0.000000 1.414214
c 2.236068 1.414214 0.000000
```





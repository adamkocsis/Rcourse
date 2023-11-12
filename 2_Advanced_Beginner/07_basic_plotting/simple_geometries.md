---
parent: Basic plotting
layout: material 
nav_order: 2
title: Simple geometries 
topic: "simple_geometries"
level: "2"
grand_parent: "Level 2 - Advanced Beginner"
---

# Simple geometric functions

Most low-level plotting functions use multiple values to so we can visualize more complex things with them. Almost all of these functions are actually made up of very simple geometric elements that can be controlled using a couple of values.

To demonstrate the basic set, let's create a background plot to work with:

```R
plot(0,0)
```

![img]({{site.url}}{{site.baseurl}}/images/plot.png)

## Plotting points

A single point can be drawn easily with the `points()` function, you just have to provide the point's x and y coordinate:

```R
plot(0,0)
points(x=0.1, y=0.5)
```
![img]({{site.url}}{{site.baseurl}}/images/points.png)

This code draws a single point at (`0.1`,`0.5`) over an **existing plot**. Note that since `points()` is a low-level plotting function, it does not redraw the plot, but always adds to the existing one!


## Plotting text

Plotting text is extremely similar; you have to provide one more argument: the text that you want to show. This is given with the `label` argument.

```R
plot(0,0)
points(x=0.1, y=0.5)
text(x=-0.5, y=0, label="Mine!")
```

![img]({{site.url}}{{site.baseurl}}/images/text.png)

## Infinite lines

In geometry, lines do not have endpoints - and the lines drawn in R (`abline()`) will share this characteristic. Lines go through the entire plotting area. Such lines can be either horizontal, vertical or angled. Horizontal lines are defined using the y coordinate (`h` argument for horizontal), and vertical lines with the x coordinate (`v` argument for vertical):

```R
plot(0,0)
abline(v=0.4)
abline(h=0)
```
![img]({{site.url}}{{site.baseurl}}/images/lines.png)

Angled lines are given using the [equation of a straight line](https://en.wikipedia.org/wiki/Linear_equation), by referring to the intercept (`a`, where the line is crossing the y axies) and the slope (`b`):

```R
plot(0,0)
abline(a=-0.3, b=0.4)
```
![img]({{site.url}}{{site.baseurl}}/images/lines2.png)

## Line Segments

It is not so much difficult draw a line segment, which has two endpoints. Segments can be plotted using `segments()`. This function has four arguments: `x0`, `y0`, `x1`, and `y1`. Note that these arguments describe two points: the endpoints of the segment: the first point is (`x0`, `y0`) and the second is (`x1`, `y1`). It is frequent in computer science to start numbering things with 0 rather than 1... 

```R
plot(0,0)
segments(x0=-0.3, y0=-0.2, x1=1, y1=0.7)
```
![img]({{site.url}}{{site.baseurl}}/images/segments.png)

## Rectangles

Rectangles are used very frequently and can be drawn using the `rect()` function. The arguments to plot rectangles are `xleft`, `xrigth`, `ytop`, and `ybottom`. You can guess what they mean - if in doubt, contrast the instructions with the plot below.


```R
plot(0,0)
rect(xleft=-0.5, xright=0.3, ybottom=0.2, ytop=0.8)
```
![img]({{site.url}}{{site.baseurl}}/images/rect.png)


# Standard arguments

You can already make quite impressive plots with these basic functions, some coordinate geometry and iteration alone. However, you might also want to configure how these functions actually work - which you can do using the arguments of `par()`, which is used configure everything happening in a plotting function. Check out the help file of this function `?par`, to see some of the these universally-used arguments. If you do not know how to configure a plot in R, betting on these will likely be successful. The most important ones are:

| argument | behaviour                            |
|----------|--------------------------------------|
| col      | The color of the object              |
| cex      | The size of the object: relative     |
| lwd      | Line width                           |
| lty      | Line type                            |
| border   | The border color, if there is a fill |

There are numerous tutorial online discussing basic R plotting. 

# Exercising plots

Plots are excellent if you want to practice basic programming (conditionals, iteration) because you see immediate feedback on whether you have correctly used the construct of your choice. Using the vectorization principles of R you usually can do such plotting much easier and faster than suggested in the exercises below.  

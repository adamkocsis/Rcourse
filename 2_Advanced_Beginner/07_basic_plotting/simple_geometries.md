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

Most low-level plotting functions rely on object structure to visualize more complex structures. Almost all of these are actually made up of very simple geometric elements that can be controlled using simple values.

To demonstrate the basic set, let's create a basic background plot to work with:

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

This code draws a single point at (0.1,0.5). Note that since `points()` is a low-level plotting function, it does not redraw the plot, but adds to the existing one!


## Plotting text

Plotting text is extremely similar: you have to provide one more argument: the text that you want to show, this is given with the `label` argument.

```R
plot(0,0)
points(x=0.1, y=0.5)
text(x=-0.5, y=0, label="Mine!")
```

![img]({{site.url}}{{site.baseurl}}/images/text.png)

## Infinite lines

In geometry, lines do not have endpoints - and the lines drawn in R (`abline()`) will share this characteristic with them: they will go through the entire plotting area. Such lines can be either horizontal, vertical or angled. Horiztonal lines are defined using the y coordinate (`h` argument for horizontal), and vertical lines with the x coordinate (`v` argument for vertical):

```R
plot(0,0)
abline(v=0.4)
abline(h=0)
```
![img]({{site.url}}{{site.baseurl}}/images/lines.png)

Angled lines are given using the [equation of a straight line](https://en.wikipedia.org/wiki/Linear_equation), by referring to the intercept (`a`) and the slope (`b`):

```R
plot(0,0)
abline(a=-0.3, b=0.4)
```
![img]({{site.url}}{{site.baseurl}}/images/lines2.png)

## Line Segments

It is not so much difficult draw in R is a line segment, which can be plotted using `segments()`. This function has four arguments: `x0`, `y0`, `x1`, and `y1`. Note that these arguments describe two points: the endpoints of the segment.

```R
plot(0,0)
segments(x0=-0.3, y0=-0.2, x1=1, y1=0.7)
```
![img]({{site.url}}{{site.baseurl}}/images/segments.png)

## Rectangles

Rectangles are used very frequently and can be drawn using the `rect()` function. The arguments to plot rectangles are `xleft`, `xrigth`, `ytop`, and `ybottom`. You can guess what they mean.


```R
plot(0,0)
rect(xleft=-0.5, xright=0.3, ybottom=0.2, ytop=0.8)
```
![img]({{site.url}}{{site.baseurl}}/images/rect.png)


# Configuring these

You can already make quite impressive plots with these basic functions, some coordinate geometry and iteration alone. However, you might also want to configure how these functions actually work - which you can do using the arguments of `par()` that is used configure everything happening in a plotting function. They tend to these basic arguments tend to be universal. If you do not know how to configure a plot in R, betting on these will likely be successful. Some of these are:

| argument | behaviour                            |
|----------|--------------------------------------|
| col      | The color of the object              |
| cex      | The size of the object: relative     |
| lwd      | Line width                           |
| lty      | Line type                            |
| border   | The border color, if there is a fill |

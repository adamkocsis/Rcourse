---
parent: Basic plotting
layout: material 
nav_order: 1
title: Plotting concepts
topic: "plotting_concepts"
level: "2"
grand_parent: "Level 2 - Advanced Beginner"
---

# About plotting in R

## Devices

R handles plots via so-called *Graphics Devices*. These devices are different outlets that we can use to do different things with the plotting instructions: for instance, we can either display them on the computer screen, or we can write them into files. 

We will look into devices a bit later - suffice it to say that if you do not specify what device you want to use, a default device will be opened for you, that will render your plot on the computer screen (either in a panel in RStudio (RStudioGD).

## Function level in plotting

In traditional (S-style) R we usually differentiate between high-level and low-level plotting functions. 
### High-level plotting functions

High-level plotting functions create entire plots based on the given arguments. These functions 
1. finalize (or erase) the existing plot,
2. create a new plot for us to work with,
3. and Draw someting on the plot for us, by calling to some [low-level plotting functions](#low-level-plotting-functions) themselves.

The most frequently used high-level plotting function in R is `plot()`. This function can be used to visualize most objects in R, and in multiple ways.

This call will make a very simple - but complete plot:

```
plot(x=0, y=0)
```

![img]({{site.url}}{{site.baseurl}}/images/plot.png)

### Low-level plotting functions

Low-level plotting functions add elements to existing plots. These can include simple geometries, text, curves, polygons - even existing images. 

Most high-level plotting functions have some low-level plotting functionality in them. For instance, the call above to `plot()` does multiple things, that you can also invoke separately:

- It initializes the plot (`plot.new()`) and sets the parameters (`par()`)
- It draws the x and y axes (`axis()`).
- It draws the box around the plot (`box()`)
- It draws x and y axis labels (`mtext()`)
- It adds a single point at (0,0) (`points()`)

To illustrate the concept and how to control these aspects separately, you can recreate the plot above like this. Execute these lines one-by-one to see how this plot can be built up from parts:

```R
plot(0,0, axes=FALSE, ylab="", xlab="", type="n")
box()
axis(1)
axis(2)
mtext(text="0",side=1, line=3)
mtext(text="0", side=2, line=3)
points(0,0)
```

![img]({{site.url}}{{site.baseurl}}/images/plot_parts.png)

*Note that we are intentionally suppressing the default plotting behaviour!*,

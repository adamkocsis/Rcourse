---
layout: exercise 
nav_order: 1
title: Read in files and execute scripts
id: 2022-12-12_read_in_files
parent: Exercise registry
---

## Instructions

The following exercises are about processing data that you have to read in from a file. For every part of the exercises you are expected to

1. Download a data file
2. Put the datafile into a specific place
2. Modify the path to the file in the code snippet, 
3. Run the code to produce a plot from the downloaded data!

* * *

## Part 1 

1. Download this file to the hard drive: [volcano.rds]({{site.url}}{{site.baseurl}}/download/volcano.rds)
2. Make sure that the file is in the `Downloads` directory (on Windows this is C:\Users\<Username>\Downloads)
3. Modify and run this bit of code until you see a nice plot appearing!

```R
volcano <- readRDS("<path to file, ending with/volcano.rds>")
filled.contour(volcano)
```


## Part 2 

1. Download this file to the hard drive: [normal.txt]({{site.url}}{{site.baseurl}}/download/normal.txt)
2. Put the file in the `Desktop` directory (on Windows this is C:\Users\<Username>\Desktop)
3. Modify and run this bit of code until you see a nice plot appearing!

```R
normal <- scan("<path to file, ending with/normal.txt>")
hist(normal)
```

## Part 3

1. Download this two files to the hard drive: [spiral_x.txt]({{site.url}}{{site.baseurl}}/download/spiral_x.txt) and [spiral_y.txt]({{site.url}}{{site.baseurl}}/download/spiral_x.txt)
2. Put the files in the same directory somewhere!
3. Modify and run this bit of code until you see a nice plot appearing!

```R
# set working directory
setwd("<path to working directory>")
x <- scan("spiral_x.txt")
y <- scan("spiral_y.txt")
plot(x,y, col="#44999911", pch=16, cex=2)
```

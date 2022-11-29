---
layout: exercise 
nav_order: 1
title: Assess the validity of file paths
id: 2022-11-29_paths_validity
parent: Exercise registry
---

## Instructions

Getting to know paths can be daunting at first - but they really important and with experience they become extremely straightfoward to use.  

* * *

# Exercise 1

We want to read in a file that is present on our hard drive here (theoretically):

```
C:\Users\Adam\Downloads\example_file.rds
```

Which of the following five entries are right for reading this file in? There is more than one good solution!

### Solution A

```R
dat <- readRDS("C:\Users\Adam\Downloads\example_file.rds")
```

### Solution B

```R
setwd("C:/Users/Adam/Downloads")
dat <- readRDS("example_file.rds")
```

### Solution C

```R
dat <- readRDS("c:/users/adam/downloads/example_file.rds")
```

### Solution D

```R
dat <- readRDS("example_file.rds")
```

### Solution E

```R
setwd("C:/Users/Adam")
dat <- readRDS("Downloads/example_file.rds")
```

* * *

# Exercise 2 

We want to read in a file that is present on our hard drive here (theoretically):

```
D:\FAU\reefs\data\Harnik2011_data.csv
```


### Solution A 

```R
setwd("D:/FAU/reefs")
tab <- read.csv("data/Harnik2011_data")
```

### Solution B

```R
setwd("D:/FAU/reefs")
tab <- read.csv("data/Harnik2011_data.csv")
```

### Solution C

```R
tab <- read.csv(D:/FAU/reefs/data/Harnik2011_data.csv)
```

### Solution D

```R
setwd("D:/FAU/reefs")
tab <- read.csv("data\Harnik2011_data.csv")
```

### Solution E

```R
setwd("D:/FAU")
tab <- read.csv(paste(getwd(), "data/Harnik2011_data.csv", sep="/"))
```


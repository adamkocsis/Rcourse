---
layout: exercise 
nav_order: 1
title: Are these functions vectorized?
id: 2024-01-01_vectorized_prediction 
parent: Exercise registry
---

# Instructions

Take a look at the function definitions below. All these functions have a primary argument `x` which is assumed to be a single value. Assess whether they can be run with immediate vectorization, and answer these questions:

1. Can the function be run with multiple values supplied as `x`?
2. If not, why? 

### A

```R
DegToRad <- function(x) x/180*pi 
```

### B

```R
NumberPositive <- function(x) if(x > 0) message("x is positive!")
```

### C

```R
CelsiusToFahrenheit <- x * 1.8 + 32 
```

### D

```R
RandomLetter <- function(x) sample(letters, x, replace=TRUE)
```


### E

```R
JustSaying <- function(x) paste("I say:", x)
```




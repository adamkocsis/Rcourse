---
layout: exercise 
nav_order: 1
title: Predict results of these function calls
id: 2022-11-06_results_of_functions
parent: Exercise registry
---

## Instructions

Predict the return value of the function calls based on these definitions:

```R

f1 <- function(x) x^2

f2 <- function(a, b) a - b + 1 

f3 <- function(x){
	val <- paste0("R would say '", x, "'.")
	return(val)
}

f4 <- function(x){
	return(x == 4)
}
```

### A

```R
f1(10)
```

### B

```R
f2(4, 3)
```

### C

```R
f3("wicked!")
```

### D

```R
f4(4)
```

### E

```R
f4(NA)
```


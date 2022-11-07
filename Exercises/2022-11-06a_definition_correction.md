---
layout: exercise 
nav_order: 1
title: Correct function definition syntax
id: 2022-11-06a_definition_correction
parent: Exercise registry
---

## Instructions

Correct the following, syntactically wrong function definitions:


### A. 

```R
# function to calculate the area area of a circle
CircleArea <- function{r} (r^2 * 3.14)
```


### B. 
```R
# function to calculate area of a rectangle
RectArea <- function(a,b} a * b}
```

### C. 

```R
CelsiusToFahrenheit <- function(celsius{
	# is the input numeric?
	if(is.numeric(celsius)){
		result <- celsius * 1.8 + 32
	# if it is not the result should be missing
	}else
		message("Non-numeric input, returning NA!")
		result <- NA
	}
	return(result)
}
```

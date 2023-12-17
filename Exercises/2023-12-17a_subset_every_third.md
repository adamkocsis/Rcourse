---
layout: exercise 
nav_order: 1
title: Subset every third value in a vector
id: 2023-12-17a_subset_every_third 
parent: Exercise registry
---

Consider this vector:

```R
x <- -100:99
```

This vector has exactly `200` elements. You received a chunk of (uncommented) code from a collaborator to process this:

```R
result <- NULL

for(i in 1:length(x)){
	if( i%%3==0 ) result <- c(result, x[i])
}
```

## Instruction

Part 1: What does this code do? Can you express it with human words?

Part 2. This code can be simplified using vectorization. Rewrite this chunk of code, without using either a `for` or `while` loop!



---
layout: exercise 
nav_order: 1
title: Number-coded message 
id: 2022-12-12b_number_coding 
parent: Exercise registry
---

# A number-coded message

The `letters` object includes the letters of the latin alphabet, with a letter at every index - which means that we can use the indices to code specific messages. 
	
Can you decode this message? 

```R
code <- c(14,15,2,15,4,25,NA,5,24,16,5,3,20,19,NA,20,8,5,NA,19,16,1,14,9,19,8,NA,9,14,17,21,9,19,9,20,9,15,14)
```

## Instructions

1. Use a `while` loop to look up the letters that are coded by the numbers and combine the letters in a character vector. Missing values (`NA`s) indicate spaces.
2. If you have vector of character strings (`x`), you can use `paste(x, collapse="")` to collapse the vector to a single value. Do that with the vector that you produced! 

	

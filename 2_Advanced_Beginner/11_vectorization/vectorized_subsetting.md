---
parent: Vectorization 
layout: material 
nav_order: 1
title: Vectorized subsetting
topic: "vectorized_subsetting"
level: "2"
grand_parent: "Level 2 - Advanced Beginner"
---

# Extracting multiple values

Consider the following example. We have a set of numbers:

```R
numbers <- c(-4, 6, -3, 5, -2, 4, -1, 3)
```

Imagine that we want a subset to get the positive numbers only. You can do this with defining a vector of the indices that point to the numbers you need.

```R
indices <- c(2, 4, 6, 8)
```

We can already make this subsetting with a `for()` loop:

```R
# the subset a container
sub <- NULL

for(i in indices){
	# the currently extracted value
	current <- numbers[i]

	# add to the container
	sub <- c(sub, current)
}
sub
```
```
[1] 6 5 4 3
```


This kind of subsetting is extremely useful, and is very frequently used - as a matter of fact, so frequently, that we never use it. The entire the construct above can be expressed with this single line of code:

```R 
numbers[indices]
```
```
[1] 6 5 4 3
```

This is a kind of vectorization: you take a simple calculation (subsetting), and you repeat it with a combination of structures - in this case vectors.






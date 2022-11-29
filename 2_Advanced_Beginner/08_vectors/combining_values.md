---
parent: Vectors 
layout: material 
nav_order: 1
title: Combining values 
topic: "combine_values"
level: "2"
grand_parent: "Level 2 - Advanced Beginner"
---

# About vectors

You can do almost everything with individual values, but the number of variables can get quite large as the complexity of the problems we want to solve increase.

R's simplest objects that consist of multiple values are **vectors**. They are fundamental to our workflowin R - as a matter of fact, they are so important they are the basic building blocks of everything. In R even simple values do not exist on their own, but they are wrapped so that they become vectors (even though such vectors only have one value). We also sometimes refer to vectors as *atomic*s, which indicates that the cannot be split further to other kinds of objects. 

In R's interpretation a vector is nothing, but a sequence of values, that have **the same type**. This means that not only the values, but vectors have types as well, which you can assess using the [previously discussed functions]({{site.url}}{{site.baseurl}}/2_Advanced_Beginner/02_types_and_variables/type_predicates.html). 

# Creating vectors

The simplest way to create a vector is via the combine (`c()`) function. This function takes individual values or existing vectors and makes a vector out of them:

```R
one <- c(0, 1)
```
```
[1] 0 1
```

The elements are combined in the sequence in which they are provided for the function. 
```R
two <- c(one, 12)
```
```
[1] 0 1 12
```

# In iteration

This we can use to store the results of our calculations, for instance when we are iterating a calculation, or if we have data to work with. This might require an empty container to start the aggregation with.

This is where `NULL` value becomes handy. We can use objects to store the lack of information, which we can use to add something to. `NULL` is the identity for combinations: combining things with `NULL` won't change their value.

```R
c(NULL, 13)
```
```
[1] 13
```

Also:
```R
n <- NULL
c(n, 45)
```
```
[1] 45
```

For instance, if we want to aggregate the states of a while loop, we can use this value to start our aggregation with:

```R

# number of iterations
n <- 4
# counter
i <- 0

# result
res <- NULL
res <- numeric()

while(i<n){
	# add the counter to the loop
	res <- c(res, i)
	# increment counter
	i <- i + 1
}
```
```
[1] 0 1 2 3
```



---
parent: Vectors 
layout: material 
nav_order: 5
title: Numeric subscript for replacement 
topic: "numeric_replacement_vectors"
level: "2"
grand_parent: "Level 2 - Advanced Beginner"
---

# Replacement 

Many calculations rely on modifying an existing object. In the case of vectors, we frequently want to modify them only in parts, i.e. **replace** elements in them. 

We indicate what we want to replace, by specifying the affected subset on the left-hand side of the normal assignment.

```R
# create a dummy
a <- 1:6
# replace the 5th element
a[5] <- 0
a
```
```
[1] 1 2 3 4 0 6
```

The interpretation of this chunk of code should be self-evident: you define the 5th element of the `a` vector to be replaced with the right-hand side of the assignment (`0`). The blueprint for such numerically defined replacement is

```
<object> [ <subscript index> ] <- <new value>
```

# Subscript values

A. If the value of the subscript index is higher than 0 and not higher than the length of the vector, you are pointing to valid indices of the vector and replacement happens as above. 

B. If the subscript index for the replacement is exactly 0, then no replacement will happen. 

C. If the subscript index for the replacement is higher than the length of the vector, then replacement will 1) **extend** the length of vector to the given index, and 2) will insert **missing values** (`NA`) into the undefined places in the vector.

```R
b <- 1:4
b[9] <- 5
b
```
```
[1]  1  2  3  4 NA NA NA NA  5
```


D. If the subscript index is negative, then the complementary set of values will be replaced (i.e. excluding the one pointed to by the index). 

```R
d <- 1:4
d[-3] <- -5
d
```
```
[1] -5 -5  3 -5
```

In this case every value but the 3rd is replaced. Note that we have replaced multiple values with the same, single value.
This is actually our first encounter with something called **vectorization**. This means that we are executing the same operation (the replacement) **multiple times**, relying solely on object structure, without explicitly defining an iteration. We will discuss the rules for this later: [see vectorization](http://127.0.0.1:4000/rkheion/2_Advanced_Beginner/11_vectorization/). 






Replace every seventh element of this vector with 0!





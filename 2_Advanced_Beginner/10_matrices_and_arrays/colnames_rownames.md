---
parent: Matrices and arrays 
layout: material 
nav_order: 3
title: Row and column names 
topic: "row_and_column_names"
level: "2"
grand_parent: "Level 2 - Advanced Beginner"
---


# Attributes of matrices

The definition of a matrix necessitates the `dim` attribute for the object. This is present in every case, when a matrix is created, no matter what function was used to create it:

```R
mat <- matrix(1:12, nrow=4, ncol=3)
attributes(mat)
```
```R
$dim
[1] 4 3
```

Similar vector's `names` that can help with finding items in a vector, matrices also benefit from using names to identify values.

# Names along the margins

The margins of a matrix refer to a dimension along which its values are organized. Two dimensional matrices have two margins: the rows and the columns (1 and 2). Accordingly, we can name the columns, using attributes similar to `names`: these atttributes are the column and the rrow names. THese are not set by default (as illustrated above), and in case they are queried with the `colnames()` and `rownames()` functions, they will be indicated to be absent by returning the value of `NULL`:

```R
colnames(mat)
```
```
NULL
```

```R
rownames(mat)
```
```
NULL
```


# Setting row and column names

We can use replacement to set both the row and the column names, similar to `names`:

```R
rownames(mat) <- letters[1:nrow(mat)]
colnames(mat) <- LETTERS[1:ncol(mat)]
```
```
  A B  C
a 1 5  9
b 2 6 10
c 3 7 11
d 4 8 12
```

Note that setting the `colnames` and `rownames` attribute will force the `show()` method to display the matrix with names along the margins, rather than the numeric subscript indices (e.g. `[,1]`).

You can query the set names the way, as with the `names` attribute:

```R
rownames(mat)
```
```
[1] "a" "b" "c" "d"
```


```R
colnames(mat)
```
```
[1] "A" "B" "C"
```


# Partial setting of attributes 

Note that both the regular `names` and the column and row names can be set partially, by replacing only specific elements. For instance if we want to keep the row names set above, but we would like to rename only the first column to something else, such as `"x"` we can do that, with replacing values in inside the attributes:

```R
rownames(mat)[1] <- "x"
mat
```
```
  A B  C
x 1 5  9
b 2 6 10
c 3 7 11
d 4 8 12
```

# Incorrect length of candidate attributes

Lets assume that we want to set the column names of this matrix:

```R
m2 <- matrix(1:10, ncol=2, nrow=5)
m2
```
```
     [,1] [,2]
[1,]    1    6
[2,]    2    7
[3,]    3    8
[4,]    4    9
[5,]    5   10
```


Using a vector of incorrect length will result in an **error**, both when the vector is too short, or too long to become the name of the margin:

```R
# Too short
rownames(m2) <- letters[1:4]
```
```
Error in dimnames(x) <- dn : 
  length of 'dimnames' [1] not equal to array extent
```

or:

```R
# Too long 
rownames(m2) <- letters[1:6]
```

```
Error in dimnames(x) <- dn : 
  length of 'dimnames' [1] not equal to array extent
```

# The truth about the row and column names: the `dimnames` attribute

This error might seem cryptic, as it refers to `dimnames` rather than row and column names. Technically speaking, both the row and column names are stored in the `dimnames` attribute, we just use the `rownames()` and `colnames()` functions to access these.

```R
attributes(mat)
```
```
$dim
[1] 4 3

$dimnames
$dimnames[[1]]
[1] "x" "b" "c" "d"

$dimnames[[2]]
[1] "A" "B" "C"
```

Now this is getting complex looking - that is because the `attributes` and the `dimnames` inside them are stored using the `list` type, which can be recognized from the dollar `$` symbols. This implementation allows more general use for n-dimensional matrices. We will learn how to interact directly with these later. 

>The `list`s are necessary because even though the same type is used for the row and column (or the nth dimension's) names, their number can be different! 







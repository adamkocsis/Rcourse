---
parent: Matrices and arrays 
layout: material 
nav_order: 2
title: Numeric subscripts for matrices
topic: "matrix_numeric_subscripts"
level: "2"
grand_parent: "Level 2 - Advanced Beginner"
---

# Subsetting matrices

The biggest advantage of using matrices is that we can find and access elements based on the margins of the matrix. Let's take a look at this matrix:

```R
mat<- matrix(11:22, ncol=4, nrow=3)
mat
```
```
     [,1] [,2] [,3] [,4]
[1,]   11   14   17   20
[2,]   12   15   18   21
[3,]   13   16   19   22
```

The `show()` method which prints out the content of the matrix gives us a hint about the dimensions and element indices of the matrix. 

# Subsetting entire rows


Let's examine what happens if we use one of the subscripts above, such as `[,1]`:

```R
mat[1,]
```
```
[1] 11 14 17 20 
```

This subsetting returns the first row of the matrix. The `1` before the comma indicates that the first column should be returned. There is nothing after the comma, which indicates that all columns need to be included in the subset.

# Subsetting entire columns

A similar pattern exists if columns are to be returned. The subscript [,2] returns the second column:

```R
mat[2,]
```
```
[1] 14 15 16
```

# Subscript blueprint

There is a comma in the square brackets, which possibly separates two integer values that represent rows and columns. The structure of a subscript is typically:

`object[<row>, <column>]`

Accessing individual elements happens with the specification of a row and column index. For instance, the value in the second row and the third columns:

```R
mat[2,3]
```
```
[1] 18
```


# Other subscript values

The examples above work if the row- and column-subscript values fall between 1 and the number of rows for the rows (the first value of the `dim` attribute), and between 1 and the number of columns (the second value of the `dim` attribute) for the number of columns. 

## Subscripts that are higher than the number of columns/rows 

If a subset if defined that does not exist because the subscript are higher than the highest available row or column indices, matrices and arrays work differently from vectors:

```R
a <- 1:4
a[5]
```
```
[1] NA
```

which results in missing values. Matrices (and arrays), on the other hand, return the iconic 'Out of bounds' error - either if the desired row, or column (or both) indices are defined:

```R
mat[4,5]
```
```
Error in mat[4, 5] : subscript out of bounds
```

This is an effective way to prevent accessing positions that are invalid. 

## 0 subscript

0 subscripts behave similarly to those in vectors: they produce empty containers that do not contain any values, and they have not much practical use:

```R
mat[0,3]
```
```
integer(0)
```

## Negative subscripts

The negative subscripts of vectors indicate the omission of values:

```R
vec <- 1:5
vec[-1]
```
```
[1] 2 3 4 5
```

They work similarly in matrices, they define the omission of entire rows:

```R
mat[-1,]
```
```
     [,1] [,2] [,3] [,4]
[1,]   12   15   18   21
[2,]   13   16   19   22
```

or columns:

```R
mat[,-1]
```
```
     [,1] [,2] [,3]
[1,]   14   17   20
[2,]   15   18   21
[3,]   16   19   22
```

or both:

```R
mat[-2,-1]
```
```
     [,1] [,2] [,3]
[1,]   14   17   20
[2,]   16   19   22
```

As the outputs show here, the results of this operation is a matrix - similar to the original object.

# The `drop` argument of subsetting

When subsetting matrices, the default behavior is to simplify the output of the object. When an individual value, row or column subset is defined, the subsetting returns a vector class (numeric, logical, character. etc...):

```R
sb <- mat[,2]
class(sb)
```
```
[1] "integer"
```

which looses its `matrix` class:

```R
# the original object
is.matrix(mat)
```
```
[1] TRUE
```

```R
# the subset 
is.matrix(sb)
```
```
[1] FALSE 
```

This is because subsetting by implicitly involves the `drop` argument, which is by default set to `drop=TRUE`, forcing the results of subsetting to drop the `matrix` class, whenever possible. 

When subsetting is applied in a programmatic context and subscripts change during the process, the result of subsetting can sometimes be either easilly simplified to a single vector (row or column) and sometimes cannot (and has to stay a matrix). If the result is sometimes simplied to a matrix and sometimes not, then further subsetting can cause issues. Consider this case:

```R
sa <- -1
partial <- mat[sa, ]
partial
```
```
    [,1] [,2] [,3] [,4]
[1,]   12   15   18   21
[2,]   13   16   19   22
```

This can be further subsetted, with matrix rules:

```R
partial[,2]
```
```
[1] 15 16
```

Contrast the case above with this scenario, when `sa` is set to `1`:

```R
sa <- 1
partial <- mat[sa, ]
partial
```
```
[1] 11 14 17 20
```

We will encounter the error with the same chunk of code:

```R
partial[,2]
```
```
Error in partial[, 2] : incorrect number of dimensions
```

This issue can be easilly evaded, with the `drop=FALSE` argumentation, that forces the output of the subsetting to conserve its `matrix` class. 

```R
sa <- 1
partial <- mat[sa, , drop=FALSE]
partial
```
```
     [,1] [,2] [,3] [,4]
[1,]   11   14   17   20
```

This result is a simple row-matrix, where the matrix-style subsetting will not cause any error:

```R
partial[,2]
```
```
[1] 14
```









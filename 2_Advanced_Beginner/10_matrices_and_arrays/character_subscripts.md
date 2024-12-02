---
parent: Matrices and arrays 
layout: material 
nav_order: 4
title: Character subscripts 
topic: "matrix_character_subscripts"
level: "2"
grand_parent: "Level 2 - Advanced Beginner"
---

# Character subscripts for subsetting and replacement

Let's consider the same matrix as before:

```R
mat <- matrix(1:12, nrow=4, ncol=3)
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


You could probably guess that the purpose of setting column and row names is in the easier identification of values based on the margin. If we want to find the value in the `c` row and the `B` column, we would either have to calculate the indices at which these columns are, which is a bit too much work. It is much easier to just refer to these with the names, i.e. using character subscripts:

```R
mat["c", "B"]
```
```
[1] 7
```

# Entire row and column subsets

Character subscripts work very similarly to numeric subscripts: you can get entire rows and columns with them.

```R
# subset to the C column
sb <- mat[, "C"]
sb
```
```
a  b  c  d 
9 10 11 12 
```

Note that in this case of subsetting one column, the resulting object **conserved** the names of the rows. Since this is simplified to a single vector (because by default `drop=TRUE`), these names are now stored in the `names` attribute of the object:

```R
names(sb)
```
```
[1] "a" "b" "c" "d"
```
 
and are no longer accessible with `rownames()`:

```R
rownames(sb)
```
```
NULL
```


If you would like to conserve the matrix-like properties, use `drop=FALSE`, as discussed earlier:

```R
# subset to the C column
sb2 <- mat[, "C", drop=FALSE]
sb2
```
```
   C
a  9
b 10
c 11
d 12
```

This will conserve both the row and the column names. (Even when only a single value is accessed!)

# Out of bounds

When you try to access a row or column that doesn't exist, subsetting with character subscripts as well will return the iconic 'out of bounds' error:

```R
# there is no U column!
mat["U", "A"]
```
```
Error in mat["U", "A"] : subscript out of bounds
```

# Duplicates in the row and column names

## **IMPORATANT NOTE** 

This section about duplicates should serve as a warning, that such duplications are possible. Try to avoid this whenever it is possible: use unique row and column names for matrices!

Similar to the `names()` function in vectors, both the `rownames()` and `colnames()` functions allow you to set names **WITH DUPLICATES** when working with matrices (*this is not true for `data.frame`s!!!*):

```R
# duplicating the first rowname
rownames(mat)[2] <- "a"
mat
```
```
  A B  C
a 1 5  9
a 2 6 10
c 3 7 11
d 4 8 12
```

If you try to access the elements with the duplicate name, you will only get **the first** match:

```R
mat["a", ]
```
```
A B C 
1 5 9 
```

This is very likely not the desired behavior, as there are multiple rows with the same name. For this reason, try to avoid using duplicates in the row and column names in matrices and arrays - and test for duplications if you are uncertain!


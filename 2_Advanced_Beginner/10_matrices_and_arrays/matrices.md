---
parent: Matrices and arrays 
layout: material 
nav_order: 1
title: Matrix basics 
topic: "matrix_basics"
level: "2"
grand_parent: "Level 2 - Advanced Beginner"
---

# Vectors

In R we use vectors to store values in a particular order, such as this sequence:

```R
a<- 101:106
a
```
```
[1] 101 102 103 104 105 106 
```

This allows easy retrieval via numeric subscripts, for instance the third value:

```R
a[3]
```
```
[1] 103
```

Or - after the assignment of names - via character subscripts:


```R
names(a) <- c("a", "b", "c", "d", "e", "f")
a["f"]
```
```
  f 
106 
```

This structure is nothing else but a sequence of values, that does not convey any information about orientation (vertical or horizontal).

However, in many cases we would like to store information that benefit from even more organization: we can add dimensions to the stored values, so we can access them in a more ordered fashion.

# The `dim` attribute

We have already seen the [`names` attribute]({{site.url}}{{site.baseurl}}/2_Advanced_Beginner/08_vectors/names.html), and how it influences the behavior of an object. Naturally there are other attributes that we can assign to the objects, which modify their behavior.

One of the most frequently used one is the `dim` (i.e. dimension) attribute. This attribute forces a vector to 'curl' up into multiple dimensions and form `matrices` and `arrays`. 

Consider this code snippet, the assignment of a `dim` attribute to a different, but similar the vector:

```R
# the simple vector
b <- 21:32
b
```
```
 [1] 21 22 23 24 25 26 27 28 29 30 31 32
```

```R
# assigning a dim attribute
dim(b) <- c(3,4)
b
```
```
     [,1] [,2] [,3] [,4]
[1,]   21   24   27   30
[2,]   22   25   28   31
[3,]   23   26   29   32
```

This is now something that we refer to as a **`matrix`**. 

```R
class(b)
```
```
[1] "matrix" "array" 
```

In R, only a two-dimensional (2D) `array` is called `matrix`, these (since R 4.0) have both `matrix` and `array` classes. Higher dimensional structures (3D, 4D, *n*D) are only `array`s (later).

### Type of values

Note that the values are the same as what they were before the assignemnt of the `dim` attribute. That is because the underlying data **is still the original vector**, we only change how it behaves. For this reason the type of the matrix is going to be the same as that of the vector (in this case an `integer` sequence):

```R
typeof(b)
```
```
[1] "integer"
```

In R `array`-class objects (because they are built on vectors), can store only a single type (which distinguishes them from `data.frame`s).

### The dimensions

There are 3 rows and 4 columns in our matrix, because of the assigned `dim` attribute, which was a vector of two values: 3 and 4. Similar to `names()`, we can query this with `dim()`:

```R
dim(b)
```
```
[1] 3 4
```

R follows a convention for the organization and display of multidimensional items: The **first dimension is the row**, and the **second is always the column**. Our matrix has three rows because the first value of the `dim` attribute was 3.

Note the order of values in the matrix: as mentioned earlier, the original object structure is still retained. The first value of the matrix is still `21` the second is `22` and so forth. For this reason the numeric subscripts that treat matrices as vectors still work (although we almost never use these - see matrix subscripts later!): 

```R
b[1]
```
```
[1] 21
```

```R
b[2]
```
```
[1] 22
```

```R
b[6]
```
```
[1] 26
```

Nevertheless, this should give you an idea about how the information is organized in this object. Matrices 'curl up' **vertically**: the first column is filled first from top to bottom, then the second column and so on. 

The product of the `dim` vector (rows*columns) tells you exactly how many number of values of the `matrix` has, which means that if you try to assign an incompatible vector as the `dim` attribute, you will get an error. For instance:

```R
u <- 1:6
dim(u) <- c(2,4)
```
```
Error in dim(u) <- c(2, 4) : 
  dims [product 8] do not match the length of object [6]
```

The error message is very accurate and informative: if cannot 'fold up' a vector with 6 values into a matrix that should have 8. 



# The `matrix()` function

Matrices are frequently created with the `matrix()` function, that makes it more apparent in the code that a matrix is getting defined. This function has multiple ways of defining matrices, but one of them is particularly convenient: defining the number of rows (`nrow`) and columns (`ncol`) explicitly: 

```R
d <- matrix(11:16, ncol=2, nrow=3)
d
```
```
     [,1] [,2]
[1,]   11   14
[2,]   12   15
[3,]   13   16
```

This function also has a switch, in case you want to override the default behavior of filling the columns first, that forces the filling of **rows first**:

```R
e <- matrix(11:16, ncol=2, nrow=3, byrow=TRUE)
e
```
```
     [,1] [,2]
[1,]   11   12
[2,]   13   14
[3,]   15   16
```

Compare this results with the one above! 


This is particularly handy if you want to create matrices that are given as code, such as this:

```R
# define a vector (only looks like a matrix)
dat <- c(
	"one", "two", "three",
	"four", "five", "six"
)
# give dimensions
d <- matrix(dat, ncol=2, nrow=3, byrow=TRUE)
d
```
```
     [,1]    [,2]  
[1,] "one"   "two" 
[2,] "three" "four"
[3,] "five"  "six" 
```





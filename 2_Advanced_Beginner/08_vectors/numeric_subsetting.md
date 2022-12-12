---
parent: Vectors 
layout: material 
nav_order: 4
title: Numeric subscripts 
topic: "numeric_subscripts_vectors"
level: "2"
grand_parent: "Level 2 - Advanced Beginner"
---

# Subsetting

We call the process of selecting and copying a part of an object **subsetting**. With **subsetting** we can isolate parts of anobject so we can do calculations on that specific part. 

The square brackets operator `[]` usually indicates a subset of an object. Within the square brackets, we use a **subscript** to indicate which part of the object we would like to reuse:

```
object [ <subscript> ]
```

# Vector numeric subscripts 

Every value in a vector has an **index**, which is a positive integer number. The first value of a vector has an index of `1`, the second one has an index of `2`, the third `3` and so on. 

If we use the **index** of a particular value as a **subscript** we will **subset** the vector to that value. 

```R
# example vector
a <- c(2,3,4,5,6)

# the third value; index=3
a[3]
```
```
[1] 4
```

This value is a vector on its own. The same idea applies to vectors of other types. 

```R
# character vector
let <- c("a", "b", "c", "d")
let[3]
```
```R
"c"
```

*In R there are two built-in vectors for letters of the latin alphabet: `letters` for the lowercase, and `LETTERS` for the uppercase characters.*

Numeric subsetting of vectors is trivial when the value is between `1` and the number of elements that the vector has. You can get this number with the `length()` function:

```R
length(let)
```
```
[1] 4
```


**Important: when you are referrening to the last element in the vector, always do it this way, never hard-code the index into your program (in the case above this would be 4). This solution works with any length, even if the vector's length changes in a program (e.g. in a loop)!**


Consequently, if you want to select the last element of a vector, you have to use:

```R
let[length(let)]
```
```
[1] "d"
```

If you want the next before last, you have to use:

```R
let[length(let)-1]
```
```
[1] "c"
```


# Non-trivial numeric subscripts

However, numeric subsetting is also understood for values other than this range. 

### Out of vector bounds: `subscript > length(vector)`


This case occurs when you would like to get a value out of a vector with an index which is higher than the number of elements a vector has. For vectors, the convention for this case is to return a **missing value** (`NA`). 

For instance if you would like to get the 20th element of the example vector above

```R
let <- c("a","b","c","d")
let[20]
```
```
[1] NA
```

### Empty subset: `subscript == 0`

The numeric subsetting with index `0` is understood as not returning any value from the vector. 

```R
a[0]
```
```
numeric(0)
```

The result indicates that the type of the vector is conserved, but it does not have any value.

You may wonder why this exists in the first place. Naturally, when the 0 is explicitly written in the code this has no meaning. But the subscript can be a changing variable as well. In these cases the 0 value might arise as a result a calculation, and this case will need to be dealt with in a sophisticated way.

```R
# for the first value
b <- 1
# a[b]

# decrementing this
b <- b-1
a[b]
```
```
numeric(0)
```


Your query will result in a missing value.

### Negative values: `subscript < 0`

Negative subscripts are non-trivial, since there cannot be negative indices of elements in a vector. Therefore, a convention is put into place: negative subscripts mean the removal of values from vector, keeping everything but the value at the index that you indicate. Using `-1` as a subscript removes the first element of the vector and keeps everything else:

```R
res <- let[-1]
res
```
```
[1] "b" "c" "d"
```

with the length being the one less than originally

```R
length(res)
```
```
[1] 3
```

If you want to remove a middle value, that is also possible:

```R
let[-2]
```
```
[1] "a" "c" "d"
```

You can remove the **last one** as well. For this we use the length of the vector:

```R
# remove last element
let[-length(let)]
```
```
[1] "a" "b" "c"
```

You an also use a value smaller than this:
```R
let[-30]
```
```
[1] "a" "b" "c" "d"
```

This however will not have any effect. Since you are referring to remove an element of a vector which does not exist, the results will be identical.

# Here is a summary of numeric subscripts

| subscript                       | result                       |
|---------------------------------|------------------------------|
| subscript < 0                   | Removal of value at index    |
| 0                               | 0-length, empty vector       |
| 1 <= subscript <= vector length | Returning the value at index |
| vector length < subscript       | `NA`, missing value          |








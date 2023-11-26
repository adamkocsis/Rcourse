---
parent: Vectors 
layout: material 
nav_order: 6
title: Names attributes 
topic: "names_attribute"
level: "2"
grand_parent: "Level 2 - Advanced Beginner"
---

# Attributes 

Attributes are pieces of added information that do not directly influence the normal behavior of an object, but can help extend their functionality and identifiability.  

Attached attributes can be queried with the `attributes()` function.

```R
# sequence of values
a <- 1:6
attributes(a)
```
```
NULL
```

Normally R objects do not get instantiated with attributes - but there are ways how we can make this happen.

# Names

The `names` attributes can be added to `vector`s and lists. They are very helpful in identifying elements. 

A `names` attribute itself is always a `character` vector, and can be assigned with using  the `names` function on the left-hand side of the normal assignment operation (technically, this is the `names<-` function).

```R
a <- 1:6
names(a) <- c("a", "b", "c", "d", "e", "f")
```
```
a b c d e f 
1 2 3 4 5 6
```

The assigned names can be queried with the `names()` function:

```R
b <- names(a)
b
```
```
[1] "a" "b" "c" "d" "e" "f"
```

Which will return character vector.

# Correct number of elements

It is logical to assume that the `character` vector assigned to be the `names` attribute should have the same length as the number of elements in the vector.

If you try to assign a longer character vector to be the names than the number of elements that you have in the vector, you will get an error message:

```R
d <- 1:4
names(d) <- c("a", "b", "c", "d", "e", "f")
```
```
Error in names(d) <- c("a", "b", "c", "d", "e", "f") : 
  'names' attribute [6] must be the same length as the vector [4]
```

If, however, you have **less** elements in the vector that was supposed to become the `names`, the final values will be filled with **missing values (`NA`)**:

```R
f <- 1:5
names(f) <- c("a", "b", "c", "d")
f
```
```
   a    b    c    d <NA> 
   1    2    3    4    5 

```

# Duplicates

Normal `names` attributes can have the same value repeated multiple times.

```R
g <- 1:5
names(g) <- c("a", "b", "c", "d", "a")
g
```
```
a b c d a 
1 2 3 4 5 
```






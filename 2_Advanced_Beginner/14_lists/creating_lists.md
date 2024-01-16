---
parent: Lists 
layout: material 
nav_order: 1
title: "Creating Lists" 
topic: "creating_lists"
level: "2"
grand_parent: "Level 2 - Advanced Beginner"
---

## Reason

Vectors in R cannot have more than a single type, which limits the cases when we can use them. They are excellent at storing homogeneous data, we can record values in sequence, and even add dimensions to define structure. However, there might be cases when we want to store different types together. 

We have already seen how we can use attributes - especially the `names` attribute to connect different types together in the same object. Lists are used under the hood to store this information.

## Simple lists

Let's assume that we have a group that has four members (Stan, Eric, Kyle and Kenny). This we we can store in a character vector very easily:

```R
kids <- c("Stan", "Eric", "Kyle", "Kenny")
```

This is easy. Let's assume that we have another set of names:

```R
parents <- c("Randy", "Sharon", "Liane", "Gerald", "Sheila", "Stuart", "Carol")
```

These two vectors have different lengths. Theoretically we could make these 4/7 length vectors columns in a matrix, but it does not make much sense, since the same-order (say third) value in them do not really make any semantic entity (which would be a row in a table).

Lists allow us to connect these two vectors together into a single object - for instance, to represent animated characters. We can create such objects with the `list()` function.


```R
southPark <- list(kids, parents)
southPark
```
```
[[1]]
[1] "Stan"  "Eric"  "Kyle"  "Kenny"

[[2]]
[1] "Randy"  "Sharon" "Liane"  "Gerald" "Sheila" "Stuart" "Carol" 
```

The `show()` method produces this complicated output, with weird double brackets `[[`. These double brackets always indicate `list`s. # List characteristics

List allows us to combine vectors into arbitrary structures. Lists are an independent type of objects in R:

```R
typeof(southPark)
```
```
[1] "list"
```

and they also have the same class:

```R
class(southPark)
```
```
[1] "list"
```

The structure of this list is actually much better visible with the `str()` function. 

```R
str(southPark)
```
```
List of 2
 $ : chr [1:4] "Stan" "Eric" "Kyle" "Kenny"
 $ : chr [1:7] "Randy" "Sharon" "Liane" "Gerald" ...
```

Lists are similar to vectors, but they are much less constrained. They have lengths, similar to vectors:

```R
length(southPark)
```
```
[1] 2
```

This might be a surprise, as `length()` does not return the total number of values in the list. It rather returns the number of 'elements', i.e. the number of objects that the list is made of: in this case the two character vectors. 

# Heterogeneous lists

Lists also allow us to store different types in the same object, like this:

```R
li <- list(letters[1:4], 1:5, c(TRUE, FALSE, TRUE))
li
```
```
[[1]]
[1] "a" "b" "c" "d"

[[2]]
[1] 1 2 3 4 5

[[3]]
[1]  TRUE FALSE  TRUE
```

This list is very general: it has three elements, a character vector with 4 values, a numeric vector with 5 values and 3 logical values. Again, this can be better seen with the `str()` function:

```R
str(li)
```
```
List of 3
 $ : chr [1:4] "a" "b" "c" "d"
 $ : int [1:5] 1 2 3 4 5
 $ : logi [1:3] TRUE FALSE TRUE
```













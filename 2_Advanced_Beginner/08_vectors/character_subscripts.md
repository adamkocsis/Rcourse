---
parent: Vectors 
layout: material 
nav_order: 7
title: Character subscripts 
topic: "character_subscripts"
level: "2"
grand_parent: "Level 2 - Advanced Beginner"
---


# Subsetting with character subscripts

Assigning names to vectors allow us to identify the subsets of vectors with the names. This is done technically with using a character value between the subsetting brackets `[]`. 

```R
a <- 1:4
names(a) <- c("a", "b", "c", "d")
a["d"]
```
```
d 
4 
```

The returned value will be a `named numeric` vector (so the names are conserved). 

# Replacement with character subscripts

Similarly to numeric subscripts, the character subscripts can also be used to perform replacements:

```R
g <- 1:4
names(g) <- c("a", "b", "c", "d")
g["d"] <- -9
```
```
 a  b  c  d 
 1  2  3 -9 
```

# Duplicates

If names are duplicated, and the duplicate name is queried, only the value that is present **at the first occurrence** of the queried value will be returned. 

```R
d <- 1:4
names(d) <- c("a", "b", "c", "a")
d["a"]
```
```
a 
1 
```

Replacement indicated the same way will also replace only the first value that occurrs at the queried character:

```R
d <- 1:4
names(d) <- c("a", "b", "c", "a")
d["a"] <- -9
```
```
 a  b  c  a 
-9  2  3  4 
```






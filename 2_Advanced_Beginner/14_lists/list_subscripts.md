---
parent: Lists 
layout: material 
nav_order: 2
title: "List element subscripts" 
topic: "list_element_subscripts"
level: "2"
grand_parent: "Level 2 - Advanced Beginner"
---

Let's create the same list as we had earlier:

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

The length of this list will be 3, as there are three elements in this list

```R
length(li)
```
```
[1] 3
```

# Numeric subscripts

We can access the list's elements by following the guidelines of the `show()` method (the result printed out to the console, when you type in an objects name). The elements of the lists start with a double bracketed indices, such as `[[1]]`. This is the subscripts to access the first element of the list, and we use it similarly to the normal vector subscripts. 

```R
first <- li[[1]]
first
```
```
[1] "a" "b" "c" "d"
```

With the double brackets `[[` we effectively retrieved the original vector, which we can confirm by looking at the type of this entry:

```R
typeof(first)
```
```
[1] "character" 
```

Then we can access any values in this objects the traditional way. For instance, if we want to access the value which is now `"d"` (the fourth value in the first list element), we can do it like this:

```R 
first <- li[[1]]
first[4]
```
```
[1] "d"
```

Actually, since the double bracket `[[` has higher precendence (because list elements can be accessed from outside to inside direction), we can succintly write the same expression as:

```R
li[[1]][4]
```
```
[1] "d"
```

This subsetting is exactly the same as the one above - just without an intermediate variable `first`: you select the first element of the list, and then the fourth value of the vector. 

# Names and character subscripts

As any other kind of R objects, lists can have attributes. For instance, similar to vectors, a `list` can have `names` attributes. By default, there is no `names` attribute defined

```R
names(li)
```
```
NULL
```

This can be defined as for vectors, by assigning a single character vector, such as:

```R
names(li) <- c("alpha", "beta", "gamma")
li
```
```
$alpha
[1] "a" "b" "c" "d"

$beta
[1] 1 2 3 4 5

$gamma
[1]  TRUE FALSE  TRUE
```


Note that the values displayed by the `show()` method have changed: instead of the double brackets `[[` you see dollars and the name value e.g. `$alpha`. This should hint at a simple way of using character subscripts already.

```R
# the first element of the list, named 'alpha'
li$alpha
```
```
[1] "a" "b" "c" "d"
```

This is actually just a succint way of using the double brackets operator `[[`, and is exactly the same as:

```R
# the first element of the list, named 'alpha'
li[["alpha"]]
```
```
[1] "a" "b" "c" "d"
```

Where we use the name as `character` value (or vector). The dollar-notation is somewhat easier on the eyes, so it is very frequently used in analytical code. This is a form of [syntactic sugar](https://en.wikipedia.org/wiki/Syntactic_sugar), built into R to make code a bit easier to read.  


# Summary 

All these different subscripting access the elements inside the list - so they can only point to exactly **one element** of the list!  


# Recursive lists

An element of a list can be an **arbitrary R object**, even other lists! For instance the list that we created earlier:

```R
nested <- list(li, 1000)
nested
```
```[[1]]
[[1]]$alpha
[1] "a" "b" "c" "d"

[[1]]$beta
[1] 1 2 3 4 5

[[1]]$gamma
[1]  TRUE FALSE  TRUE


[[2]]
[1] 1000

```

Now this is gettin













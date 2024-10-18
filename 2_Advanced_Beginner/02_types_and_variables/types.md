---
parent: Types and Classes 
layout: material 
nav_order: 1
title: Types in R
topic: "types"
level: "2"
grand_parent: "Level 2 - Advanced Beginner"
---

# Data in R - Types

Every bit of data that R users interact with are derived from some basic forms or `type`s. These define what the basic values can be, how they are stored and organized by the computer. Every data value has a type, which can be accessed with the `typeof` function.

```R
typeof(12)
```

```R
typeof("me")
```


In R there are 6 **basic** data types: 

- `logical`
- `integer`
- `double`
- `complex`
- `character`
- `raw`


There are some other very imporanty types in R, such as `builtin` (integrated functions), `closure` (e.g. user-defined functions), `expression`, `environment`, `language` (formulae), `list`, `symbol`, `S4`, ... which will be discussed at a later point.  

## `logical`

Logical values are the most straightforward of the data types. These can take only two different values: `TRUE` and `FALSE`, which have the numeric equivalents of `1` and `0`. Logical values are also called 'booleans' as these form the basics of boolean logic and algebra. These are part in most programming languages

```R
typeof(TRUE)
```


## `double`

Similar to other programming languages, R stores integers and floating point data differently. The word `double` refers to double-precision floating point numbers (decimals). Whenever a simple number is used in an R expression (even if it an integer number!), it will be implied to be a `double`.


```R
# an integer nuber
typeof(12)
```


```R
# an actual decimal point number
typeof(12.3)
```

R also accepts and recognizes scientific notation for numbers. In such cases the exponents of `10` are given after a lowercase `e` symbol:

```R
# 45600000 in scientific notation
typeof(4.56e7)
```



## `integer`

Most R operations with numbers rely on doubles, but some actually need and use integers. Users usually interact with integers that result (return) from a function (frequently in relation to indexing of vectors), for instance:


```R
# an R vector
typeof(which(TRUE))
```


In cases these are explictly need to be defined, the use of integers can be indicated with a captial 'L' that follows the number.

```R
# the integer 6 
typeof(6L)
```


## `complex`

R was designed for statistical applications and have very high capacity to work with linear algebra, where complex number frequently appear. In case these are needed, they can be indicated with the usual notation: the real part of the number is followed by an imaginary number, which are separated by a plus (`+`) sign. The imaginary component ends with `i`, the square root of `-1`.  

```R
typeof(3+-4i)
```


## `characters`

Character types are used to store text items. These allow any kind of characters, the basic data item is a string of characters, also called a 'character value'.


```R
# single character strings
typeof("a")
```


```R
# longer character strings, with any weird characters
typeof("!fá7˘$")
```

## `raw`

Raw types are used to store lower level data objects (raw bytes). What this means is that no encoding or structure is enforced on the data. In practical data analyses this is almost never encountered and its use is not a beginner subject.

# Class

Classes are big thing in what is called object-oriented programming, which R represents to some extend. The idea is that everything you interact with (e.g. variables and functions) is an **object**, it has a name, and some details. These are made following a structural definition called a `class`. In R, classes are used primarilly so users and instructions can recognize what can be done with an object. These classes can be accessed with the `class` function:

```R
class(TRUE)
```

When it comes to simple objects, classes are the same as the types. We can, however, build up very complex classes from the combinations of the basic types, (usually by including them inside the `list` and `S4` types, that allow combination of various types). It is a good idea to be aware of the class of your object! The function `str` can also be used to access the class information, which will be very useful in inspecting more complex objects:

```R
str(TRUE)
```


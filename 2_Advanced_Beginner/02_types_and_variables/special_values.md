---
parent: Types and Variables 
layout: material 
nav_order: 5
title: Special Values 
topic: "special_values"
level: "7"
grand_parent: "Level 2 - Advanced Beginner"
---

# Missing values (`NA`)

**Missing values** are the most frequently used special values in R. They are denoted as `NA`, which stands either for `Not available` or `Not Applicable`.

A single `NA` on its own defaults to a `logical` type (in vectors, they are adopt the type o f the vector).

```R
typeof(NA)
```


**Missing values** represent the presence of undefined information. For this reason, the usual behaviour of `NA`s is to propagate themselves: if you use it as an input to a function or operator, you usually get a missing value as a result:

```R
4 + NA
```

```R
exp(NA)
```

You can always detect the presence of missing value with the `is.na(x)` function, which returns `TRUE` in two cases: when x is a `NA` or the even more special `NaN` value.

# Infinites (`Inf`)

Computers cannot calculate numbers with absolute precision, and their ranges have a number. There are also special cases when the results of a calculations cannot be represented by proper numbers.  

The most characteristic case in R is the infamous case of division by 0. Most programming languages cannot tolerate this, but R has a special value to denote the result of such a calculation: the infinite value: `Inf`.

```R
10/0
```

These values are signed, negative infinites are also possible:

```R
-10/0
```

*Note that these results are symbolic presentations of the occurrences of these calculations, representing that you divide a number with an infinitely small number!*

You can detect these value with the function `is.infinite(x)`

```R
is.infinite(-Inf)
```

# Non-number values (`NaN`) 

These values appear occasionally, when you are doing calculations with infinites (`Inf`). The value `NaN` stands for `Not a Number`. This can occur in those special cases when you divide 0 by 0 or when you divide with `Inf` with `Inf`:


```R
Inf/Inf
```

```R
0/0
```

You can detect these specifically with the function `is.nan(x)`, which will be `TRUE` only in cases when x is `NaN`:

```R
is.nan(NaN)
```

You do not need to be particularly aware of these values, as they practically behave like missing values. The `is.na()` function will also detect them, and will return a `TRUE`:

```R
is.na(NaN)
```

# `NULL`s

In contrast to **Missing values**, `NULL`s represent the absence of information. This will make more when we build more complicated objects such as proper ``vectors`` and ``lists``.

Nevertheless, thes values can be detected with the function `is.null(x)`:

```R
value <- 12
is.null(value)
```


```R
value <- NULL
is.null(value)
```

---
parent: Types and Variables 
layout: material 
nav_order: 2
title: Variables 
topic: "variables"
level: "2"
grand_parent: "Level 2 - Advanced Beginner"
---

# Variables

Variables allow us the access of values with a name (key-value relationship). This also allows us to use the same expression to do a the same calculation with different data:


```R
x <- 4
x * x
```

Reusing the same variable with a different value:

```R
x <- 7 
x * x
```

Values are bound to variables in a process called **assignment**. This is indicated with the assignment operator `<-` (left chevron and a hypen). The place to the left of the operator is where (also called l-value) the values on the right-hand side (r-value) are assigned. 

As illustrated above, the contents of a variable can change with repeated assignment, which will override the previous assignment.

## Variable names

Because the R parser is designed to recognize some built-in things, not all variable names are possible:

- Variables cannot have white-space characters in them, e.g, space, tab, etc.
- Variables cannot contain operators like (`+`, `-`, `%`, `!`), braces or similar glyphs (e.g. comma, semicolon). Only alphanumeric characters are allowed, with the inclusion of `_`, `.` (I personally discourage the use of the period, unless explicitly intended to be used in S3 method dispatch).
- Variables cannot start with a number character (but can include them!)
- Variables names are case-sensitive. 

Naming variables is a never-ending challenge in programming. Finding good variable names is very important for the legibility of the code, and it is often required to use more than one word to accurately name a variable. It is recommended to use a [convention](): most R users use `snake_case` or `camelCase`. 


## Variables and values

Once a value is bound to a variable, using the variable name instead of a value will result in an equivalent calculation.

THere is no difference between

```R
4 * 4
```

and 

```R
x <- 4
x * x
```

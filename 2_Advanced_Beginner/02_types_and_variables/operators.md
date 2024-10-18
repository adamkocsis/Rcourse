---
parent: Types and Variables 
layout: material 
nav_order: 3
title: Operators 
topic: "operators_basics"
level: "2"
grand_parent: "Level 2 - Advanced Beginner"
---

The simplest R commands use operators to do calculations with the data. Operators are glyph characters that indicate processes to be done with data or variables. 

```R
4 * 3
```

In the case above (multiplication): the elements of the expression are:
```
<operand> <operator> <operand>
```

## Operator types

Operators can be categorized based on  two major features:
1. The **number of data values** that it uses: the **number of operands**. In base R, operators are either *unary*, *binary*, using either one or two operands, respectively. Some other languages (like C) has *ternary* operators. Extensions packages exist that implement ternary operators in R, e.g [`rtern`](https://cran.r-project.org/package=rtern).
2. The **type** that is *returned* by the process (which can be different from the type of the operands!)

## 1. Examples based on the number of operands

### Unary operator

The most commonly used unary operator is the **NOT** operator `!`. It uses a single operand, which it will invert:

```R
!TRUE
```

### Binary operator

Most operators are binary: one operand preceeding another following the operator. Most mathematical operators are binary:

```R
76 + 3
```



## 2. Operators based on types

The most imporant operators in R are either logical or numeric (return a number type). The most important ones are discussed in the following sections.

{: .note }
Behind every operator there is actually a function call. We use operators to make our code easier to read.


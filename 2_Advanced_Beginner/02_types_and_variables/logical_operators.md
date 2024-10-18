---
parent: Types and Variables 
layout: material 
nav_order: 4
title: Logical Operators 
topic: "logical_operators"
level: "2"
grand_parent: "Level 2 - Advanced Beginner"
---

# Operators expecting logical input

## Unary

The logical not operator `!` reverses the value of `TRUE` or `FALSE`:

```R
!TRUE
```

and:

```R
!FALSE
```

## Binary logical operators

### AND

| statement       | result  |
|-----------------|---------|
| `TRUE & TRUE`   | `TRUE`  |
| `FALSE & TRUE`  | `FALSE` |
| `TRUE & FALSE`  | `FALSE` |
| `FALSE & FALSE` | `FALSE` |

### OR

This is also known as the 'inclusive' OR operator.

| statement       | result  |
|-----------------|---------|
| `TRUE | TRUE`   | `TRUE`  |
| `FALSE | TRUE`  | `TRUE` |
| `TRUE | FALSE`  | `TRUE` |
| `FALSE | FALSE` | `FALSE` |

This list cannot be complete without **XOR** (the exclusive or) operator. R, however, does not actually have an operator for this, but use the function `xor()`.

| statement           | result  |
|---------------------|---------|
| `xor(TRUE, TRUE)`   | `FALSE` |
| `xor(FALSE, TRUE)`  | `TRUE`  |
| `xor(TRUE, FALSE)`  | `TRUE`  |
| `xor(FALSE, FALSE)` | `FALSE` |

# Operators with a wider range of operands 

## Equals 

The two equation signs `==` is the equals operator and will return in either a `TRUE` or `FALSE` value, which is self-explanatory. The process of checking whether two values are equal is not dependent on their type. We can use this operation with any of the basic types:

On `numeric` types:

```R
1 == 4
```

On `logical` types

```R
x <- TRUE
y <- FALSE
x == y
```

On `character` types:

```R
"ad" == "ad"
```

## Not equal to 

The **enot equal to** operation is the combination of **equals** and **not**: it will always be the reversed value of the **equals** operation:


```R
!("ad" == "ad")
```

and it is notated similary:

```R
"ad" != "ad"
```


## Greater, lesser, greater or equal to, lesser or equal to

Numerical comparisons are implemented with the binary operators `<`, `<=`, `>`, `>=`. When applied to number types, their meaning follows mathematical logic:

```R
4 <= 6 
```


```R
-4 > 6 
```

They can also applied to character types they indicate alphabetical order. Using these is not very frequent in practical data analyses - and you need to know what you are doing!

# Using different types

Generally, it is highly recommended **NOT TO MIX TYPES** when using such operators. Such statements provide interesting insights into how R implements *type casting* (the explicitly invoked changing of types), which is a more advanced subject. Some cases are used in practical data analyses though, which can be explicated with some examples. Meditate on the results of the following statements:

```R
TRUE == 1
```

```R
FALSE == 1
```


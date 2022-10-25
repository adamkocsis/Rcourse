---
parent: Types and Variables 
layout: material 
nav_order: 3
title: Logical Operators 
topic: "logical_operators"
level: "2"
grand_parent: "Level 2 - Advanced Beginner"
---

# Unary

The logical not operator `!` reverses the value of `TRUE` or `FALSE`:

```R
!TRUE
```

```R
!FALSE
```

# Binary

### AND

| statement       | result  |
|-----------------|---------|
| `TRUE & TRUE`   | `TRUE`  |
| `FALSE & TRUE`  | `FALSE` |
| `TRUE & FALSE`  | `FALSE` |
| `FALSE & FALSE` | `FALSE` |

### OR

| statement       | result  |
|-----------------|---------|
| `TRUE | TRUE`   | `TRUE`  |
| `FALSE | TRUE`  | `TRUE` |
| `TRUE | FALSE`  | `TRUE` |
| `FALSE | FALSE` | `FALSE` |

### XOR (Exclusive or) 

We do not have an operator for this, but use the function `xor()`.

| statement           | result  |
|---------------------|---------|
| `xor(TRUE, TRUE)`   | `FALSE` |
| `xor(FALSE, TRUE)`  | `TRUE`  |
| `xor(TRUE, FALSE)`  | `TRUE`  |
| `xor(FALSE, FALSE)` | `FALSE` |

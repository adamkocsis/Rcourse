---
parent: Types and Variables 
layout: material 
nav_order: 6
title: Type detection 
topic: "type_detection"
level: "2"
grand_parent: "Level 2 - Advanced Beginner"
---

# Detecting types 

Although we have the useful `typeof()` function, it is useful to simplify the detection of types.

There is a group of functions that help us with type detection, keeping things simple and help with code readability. These functions express an expectation that is being tested, for instance that the `type` of a piece of data is `character`. This test can result in either `TRUE` or `FALSE`, a logical value. We refer to such functions as **binary predicates**, indicating that the function will give us a binary (logical) value, that tell us whether the condition expressed by the function is true or not. 

These functions are very easy to use and remember:

| type        | predicate                  |
|-------------|----------------------------|
| `logical`   | `is.logical()`             |
| `integer`   | <sup>*</sup>`is.integer()` |
| `double`    | <sup>*</sup>`is.double()`  |
| `complex`   | <sup>*</sup>`is.complex()` |
| `character` | `is.character()`           |
| `raw`       | `is.raw()`                 |
| `list`      | `is.list()`                |

<i><sup>*</sup> We usually use `is.numeric()` instead of these, as in most applied contexts it is not important whether a type is `integer` or `double`. </i> The word `numeric` refers to a class, rather than to a type (later). 

You get the idea for the naming (actually there are many more such functions which we can use to detect special values and classes).

Using these functions is also quite logical:

```R
is.logical("a")
```

```R
is.logical(TRUE)
```

```R 
is.numeric(4)
```


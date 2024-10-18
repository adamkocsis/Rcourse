---
parent: Types and Variables
layout: material 
nav_order: 6
title: Mathematical functions 
topic: "mathematical"
level: "2"
grand_parent: "Level 2 - Advanced Beginner"
---

# Functions in general 

In mathematics, we use *functions* to express that we want to map a specific result to specific input parameters. Every calculation that we do is actually the result of a function (even those of operators, we just use operators to make our code look nicer).

This is a simple mathematical function call:

```R
abs(x = -5)
```

That return the absolute value of its **argument** *x*, which is defined to be `-5` (the result is `5`). This statement is resuing pre-defined instructions, which are stored in a *function* object. We can try to show the contents of this function by typing in its name to the console:

```R
abs
```

This will print out the instructions that the function is made up. In this case the function integrated deeply into R (indicated by the ".Primitive"), and we cannot inspect what the function is doing. It has a type of `builtin`:

```R
typeof(abs)
```

We can, however, display the contents of user-defined functions (which have another type called [`closure`](https://en.wikipedia.org/wiki/Closure_(computer_programming))). The class of these objects is `function`:

```R
class(abs)
```

For us, the interesting thing is that we can reuse instructions by **calling** to a function. Function calls are indicated by the **immediately following** opening parenthesis `(`. In every case, when we see a name followed by such a character, we can make sure that it is a function. 


# Mathematical functions

Mathematical functions in R always have a return value: which means that when the calculation is done, the result of the calculation is made avaiable for future use. It will be shown in the console (example above), unless it is getting used by another function or assigned to a variable. 

There are numberous mathematical functions in R. Most of them have a single argument (input), but some of them can have more. The most important ones are:

| function                  | use case       | name                        |
|---------------------------|----------------|-----------------------------|
| `abs`                     | `abs(-8`)      | Absolute value of a number  |
| `sign`                    | `sign(2)`      | Sign of a number            |
| `exp`                     | `exp(2)`       | Euler number exponentiation |
| `log`, `log10`            | `log(exp(2))`  | Logarithms with given base  |
| `factorial`               | `factorial(4)` | Factorial function          |
| `sin`, `cos`, `tan`       | `sin(0)`       | Trigonometric functions     |
| `asin`, `acos`, `atan`    | `asin(1)`      | Inv. trig. functions        |
| `sinh`, `cosh`, `tanh`    | `sinh(0)`      | Hyperbolic functions        |
| `asinh`, `acosh`, `atanh` | `asinh(0)`     | Inv. hyperbolic functions   |
| `choose`                  | `choose(5,2)`  | Choose (combinatorics)      |


... and more!


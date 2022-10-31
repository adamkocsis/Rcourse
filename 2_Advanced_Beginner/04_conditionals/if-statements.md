---
parent: "Conditionals"
layout: material 
nav_order: 1
title: If statements 
topic: simple_if_statements
level: "2"
grand_parent: "Level 2 - Advanced Beginner"
---

Conditionals represent forks in the flow of a program or program. When a condition is fulfilled, one thing happens, but only then. Without conditional statements, programs would be much more boring. 

# The use of of `if`

`if` is a keyword, that indicates such potential forks:

```R
feedback <- TRUE
if(feedback) message("Feedback is printed to the console")
```

The example above is the simplest possible case for using a conditional. A message is printed to the console, when the value of `feedback` is `TRUE`, but only then. 

`if()` expects a single logical value (either `TRUE` or `FALSE`), which we usually calculate using function that return a logical value (e.g. predicates) or a logical operator.


```R
# using the equation operator

# TRUE case
a <- 12
if(a==12) message("If a is 12, feedback is printed to the console")

# FALSE case
a <- 8
if(a==12) message("If a is 12, feedback is printed to the console")
```

```R
# using  function
# TRUE case
a <- NULL
if(is.null(a)) message("If a is NULL, feedback is printed to the console")

# FALSE case
a <- TRUE
if(is.null(a)) message("If a is NULL, feedback is printed to the console")
```

# Syntactic blueprint

These commands have the same general blueprint, which can be summarized as

```R
# Don't run
if( <condition> ) <command(s)>
```

The condition goes between the parentheses (`()`) which are followed by regular R statements. 

If there is just one command that we want to execute (like the example above), we sometimes put statements on one line.

If there are multiple commands that we want to condition, then they need to be put into braces (`{}`).

```R
# Don't run
if( <condition> ){
	<command(s)>
	<command(s)>
	<command(s)>
}
```

The use of braces indicate to R that we want to execute commands as a single entity - they belong together and that the if condition appies to all instructions. The sets of commands that are tied together in such a way is called a **block of code**.

# Special values in `if()` statements

Again, `if()` expects a single logical value. This means that using missing values (`NA`) or `NULL`s will trigger errors.

```R
# Will trigger error 
if(NA) message("Impossible!")
```

```R
# Will trigger error 
if(NULL) message("Impossible!")
```


*Side note: numbers including `Inf` will work, because they can be coerced to logical `TRUE` values without problems. We will look at such conversions later.*


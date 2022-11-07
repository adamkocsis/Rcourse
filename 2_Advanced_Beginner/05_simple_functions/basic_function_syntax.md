---
parent: "Simple functions"
layout: material 
nav_order: 2
title: Basic Function Syntax
topic: basic_function_syntax 
level: "2"
grand_parent: "Level 2 - Advanced Beginner"
---

# Basics

Functions are defined using the ***function*** keyword. Here is a simple general example:

```R
# 1. function definition (most compact)
Area <- function(r) r^2 * 3.14

# 2. function call
Area(r=10)
```

First you define the function ***Area()*** (1), and then, later in the program you you call to it (2). Note that it doesn' matter how far the function definition is from its call, but in R you must define the function **before** you call to it.



# The blueprint

The basic blueprint for functions is the same in all cases. 

```
function( <arguments> ) <instructions>
```

Functions are regular objects, if you do not assign them to a name, then you are not able to use it (ccall to it) - altough there are cases when you embed functions in other expressions making this not important. 

But in most cases you have to name your functions... and in 99% of the cases you have multiple instructions, making it necessary to use blocks: 
```
name <- function( <argument>, <argument>, ...){
	<instruction>
	<instruction>
	<instruction>
	<instruction>
} 
```


# What is happening in a function?

Let's look at the definition of the **Area()** function again, now written out in multiple lines (works just the same as the one above):


```R
# 1. function definition
Area <- function(r) {
	# hand-defined pi here
	PI <- 3.14
	# the actual calculation
	result <- r^2 * PI
	# the return value
	return(result)
}

# a random calculation
two <- 1 + 1

# the calling to the function
circle <- Area(r=two)
```


You can take the entire block of code above, and run it in R. 

The important thing to remember is that in base R, all instructions are running in linear sequence, one following the other. Just imagine an invisible indicator which line is getting run after which. 

1. First, R will process the definition, line-by-line, but nothing will happen until the final, closed brace is entered. After the function is defined, the instructions will be stored and rendered to the name `Area`.

2. Then the calculation of `two` will take place. Comments and empty lines are ignored.

3. When the execution of the function call is reached, many thing will happen:
 - The expression is parsed, R will look for what the names and symbols mean (whether everything is defined or not)
 - R will realize that you are calling to function (which you have defined). It will create a new 'frame' (*environment*) for the function to work in. This is  like going to a different table where whatever you do can be totally separated from the rest of your work.
 - Then it will look for the arguments passed to the call, and will create a copy of the objects you use, and rename them so you can reach them with the name of the argument.
 - Then every line of the function will be copied/used from the definition, until the very last instruction. Everything happens on the dedicated table/frame of the function.
 - If you have a `return` value (defined with ```return()```), that is 'saved' and will be the result of the function. In this case, this is `12.56`. After this, R destroys every object that the function created (*exits the scope*): `PI` and `RESULT`.
 - Then the value `12.56` is assigned to the name `circle`.
 
 



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

Functions are defined using the ***function*** keyword. Here is a simple, very general example:

```R
# 1. function definition (most compact)
Area <- function(r) r^2 * 3.14

# 2. function call
Area(r=10)
```


```
314
```

First you define the function ***Area()*** (1), and then, later in the program you you call to it (2). Note that it doesn't matter how far the function definition is from its call, but in R you must define the function **before** you call to it.  



# The blueprint for function definition

The basic blueprint for functions is the same in all cases. 

```
function( <arguments> ) <instructions>
```

Functions are regular objects, if you do not assign them to a name, then you are not able to use it (call to it) - altough there are cases when you embed functions in other expressions making this not important. 

But in most cases you have to name your functions... and in 99% of the cases you have multiple instructions, making it necessary to use a block: 
```
name <- function( <argument>, <argument>, ...){
	<instruction>
	<instruction>
	<instruction>
	<instruction>
} 
```

The function's *arguments* provide ways to influence how the instructions behave. We can pass already existing values as input for the instructions, which become the *arguments* of the function. In the case above, the function `Area()` has a single argument `r`, which defines the radius of the circle. This is a single number, without which you cannot execute the calculation of an area. The area is also entirely dependent on the radius: you can say that *the area is a function of the radius*. 

 

# Functions calls 

Calls to functions are recognizable from the parentheses `()` that immediately follow the name of the function. The instructions are run only when the function call happens and not before. Inside the parentheses we can provide values for the functions arguments.  

The blue print for function calls is:

```
<functionName>(<argumentName> = <argumentValue>)
```

```R
Area(r=1)
```

```
3.14
```

In this case, we invoke the area calculation with the radius of `1`, explicitly defining the `r` argument to be `1`, using the equation `=` symbol. The name of the argument is always on the left-hand side, and the value to be assigned to it is on the right-hand side. Multiple arguments are separated with commas (`,`). 

```
<functionName>(<argumentName> = <argumentValue>, <argumentName> = <argumentValue>, <ADDITIONAL PAIRS> )
```

# Functions as objects 

Without parentheses, you are just referring to the function's name as an object. If you write the name of the function into the console without these, R will just invoke `show()` on the object name and display its contents to the console. For instance in the previous case: 

```R
Area
```

```
function(r) r^2 * 3.14
```

Which is the same as:

```R
show(Area)
```

```
function(r) r^2 * 3.14
```

If I want to execute the instructions of a function, I have to call to it. Note that, `show()` is also a function, which is defined by the programmers of R and is part of the `base` package. Note that in the case when we call to it, we do not give explicit listing of arguments (with the equation symbol), in the case above this would be `show(object=Area)`. If the matching of values (in this case the `Area` object) can arguments is trivial, then we don't need to provide what arguments we are defininig. If there are multiple arguments and no clear mapping is given, the **order of the values in the parentheses** will determine which value is which argument. 



# What is happening during a function call?

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

3. When the execution of the function call is reached, many things will happen:
 - First, the expression is parsed, R will look for what the names and symbols mean (whether everything is defined or not)
 - R will realize that you are calling to function (which you have defined). It will create a new 'frame' (*environment*) for the function to work in. This is like going to a different table where whatever you do can be totally separated from the rest of your work.
 - Then it will look for the arguments passed to the call, and will **create a copy** of the objects you use, and rename them so you can reach them with the name of the argument. In this specific case, the value of the variable `two`, which is `2` is assigned to `r`. 
 - Then every line of the function will be used from the definition, sequentially run until the very last instruction (or until `return()` is encountered). Everything happens on the dedicated table/frame of the function. First `PI` is assigned a value of `3.14`, then `result` is calculated.
 - If you have a `return` value (defined with ```return()```), that is 'saved' and will be the result of the function. In this case, this is `12.56`. After this, R destroys every object that the function created (*exits the scope*): `PI` and `RESULT`, but it keeps the value to be returned: `12.56`.
 - Since we assign the return value to an object with `<-`, the value `12.56` is assigned to the name `circle`.
 
 

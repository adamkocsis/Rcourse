---
parent: "Conditionals"
layout: material 
nav_order: 3
title: Nested if statements 
topic: "nested_if_statements"
level: "2"
grand_parent: "Level 2 - Advanced Beginner"
---

# Nesting 

This concept is common in mathematical expressions: we can insert a pair of parentheses into another pair to indicate the order of operations. 

```R
b <- (1 + (12 + 4) * 3) * 4
```

In R blocks can nested as well, which are indicated by pairs of braces in other braces:

```
# this won't run, this is a just a structure
{
	<commandA>
	<commandB>
	<commandC>
	# here is a block of code, inside the block
	{
		<commandD>
		<commandE>
		<commandF>
	}
}
```

The idea is that R will think that the **block of code** is just **one command.**

*Note the use of indentation!* When we have lots of nested structures, we frequently use indentation to make our code readable.

# Nesting `if()` statements

If you want't one ore multiple statements to run conditionally that if fine. All you have to do is to put the `if()` before the command or block. Note that the only change to the previous blueprint is that the `if()` condition is now added the inserted block.


```
# this won't run, this is a just a structure
{
	<commandA>
	<commandB>
	<commandC>
	# here is a block of code, inside the block
	if( <condition> ){
		<commandD>
		<commandE>
		<commandF>
	}
}
```

In this example, commmands `<commandA>` `<commandB>` and `<commandC>` will run in all cases, but  `<commandD>` `<commandE>` and `<commandF>` will run only, if `condition` is true. 

This is the way how you can embed one if statement in another:

```R
# this won't run, this is a just a structure
if( <condition1> ) {
	<commandA>
	<commandB>
	<commandC>
	# here is a block of code, inside the block
	if( <condition2> ){
		<commandD>
		<commandE>
		<commandF>
	}
}
```

Now the execution of the entire block is conditioned on `<condition1>`. 

Here is an actual example in R:

```R
input <- 12

# outer condition
if(is.numeric(input)){

	# command 1
	message("We have entered the first block!")
	message("The input is numeric!")

	# command 2 
	# Inner condition the whole block is one command!
	if( input > 0 ){
		message("The value is larger than 0!")
	}	
}

```


You can nest such blocks as deep as you want, but note that after 4-5 levels the code becomes practically unreadable and tend to be very-very long.

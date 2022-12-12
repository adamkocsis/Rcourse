---
parent: Iteration with <tt>for</tt> 
layout: material 
nav_order: 4
title: The definition of a <tt>for</tt> loop 
topic: "definition_of_a_for_loop"
level: "1"
grand_parent: "Level 2 - Advanced Beginner"
---

# Background - Printing elements of a vector to the console

If we know how to access one element in a vector, we know how to access all of them: with iteration!

Let's assume that we have a vector:

```
a <- c(6,5,4,3,2,1)
```

If we would like to print a particular element (for instance the third) of this vector to the console, we have to use a single numeric value as a subscript:

```R
message(a[3])
```
```
4
```

To repeat this process for the whole vector, we have to change the subscript in every iteration, and let it take up values from `1` to `length(a)`. This we can already do with a `while()` loop:

```R

# start counter with 1
counter <- 1

# the actual iteration starts here
while(counter <= length(a)){
	# the counter-th element of the vector
	i <- a[counter]

	# the important bit:
	message(i)

	# increment the counter
	counter <- counter + 1
}

```
```
6
5
4
3
2
1
```

which means that we repeat the `message()` function for every elemement of the vector. 

# The Syntax of the `for()` loop

Note, that the number of elements in the vector defines the number of iterations that we do. This means that we can use the vector itself to define the loop, rather relying on counting and a condition.

This particular structure occurrs so frequently that we have a dedicated contstruct to implement this, which is the `for()` loop. The exact same loop as above can be written as:

```R
for(i in a){
	message(i)
}
```

The only difference there is, that we do not have access to `counter` in the case of the for loop, that is treated internally. 

What happens in this case is that when R sees the `for` keyword,
1. in the first iteration it will assign the first value of `a` to `i`, in the second, the second, etc - if you are doing the nth iteration, it will assign the nth number.
2. Runs all the instructions in the block (in this case this is just a message)
3. It will jump back to the beginning of the loop 
4. steps 1-3 are repeated as many times, as many values there are in `a`.
5. If `a` has no more values, the loop is finished, and program moves on.

The basic blueprint for the `for` loop is:

```
for(<changing variable> in <object to iterate by>) <command or block of commands>
```



# Comparison between `while` loop and `for` 

You will see the `for` loop much more frequently than `while` because it is easier to type - and also easier to understand: whenever you want to repeat an instruction **for** every element of a vector (or `list` - later!), you use a `for` loop.

|                      | `while`                                            | `for`                             |
|----------------------|----------------------------------------------------|-----------------------------------|
| Frequency            | rarely                                             | often                             |
| Definition           | condition                                          | structure of object               |
| Number of iterations | not necessarily known at the beginning of the loop | known at the begiinning of a loop |







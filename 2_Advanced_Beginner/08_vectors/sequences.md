---
parent: Vectors 
layout: material 
nav_order: 3
title: Sequences
topic: "sequences"
level: "2"
grand_parent: "Level 2 - Advanced Beginner"
---

# Sequences

In plain language, sequences are series of numbers that are connected by a rule. In the most frequent cases this rule is based on addition and subtraction. The simplest sequence is a series of natural numbers, for instance:

```R
c(1,2,3,4)
```
which can be defined by the rule that you get an element if you add `+1` to the previous value. This can be easily generalized by iteration. Given this simple case, you can define a sequence by looking at the starting number (**start**) the overall length (**n**):

```R
# the value to start with
start <- 4
# The number of times the process needs to repeat (length)
n <- 5
# starting the loop
result <- start
count <- 1
# the iteration itself
while(count<n){
	# add the next value 
    result <- c(result, start+ count)
	# increase counter 
    count <- count +1 
}
result
```
```
[1] 4 5 6 7 8 
```

With only slight modifications, this can be changed to be based on the start and end points:

```R
# starting number
start <- 4
# ending number
end <- 8
# the number of iterations
n <- end-start+1
# start of loop
result <- start
count <- 1
while(count <n){
	# add the next value 
    result <- c(result, start+ count)
	# increase counter 
    count <- count +1 
}
result
```
```
[1] 4 5 6 7 8
```

These solutions assume that `end` is larger than `start`, but this is not guaranteed. Also, there is a considerable amount of coding required for a relatively simple concept.

# The `seq()` function

Such sequences are very frequently used in R, which is why there is a dedicated function to make them: `seq()`. The `seq()` function needs at least 2 arguments: `from` and `to` - which assuming a difference between every element (step size) of 1, produces trivial results:

```R
seq(from = 1, to = 5)
```
```
[1] 1 2 3 4 5
```

### Varying step size

You can also vary the step size of the sequence with the `by` argument.

```R
seq(from = 1, to = 9, by=2)
```
```
[1] 1 3 5 7 9
```

Negative step sizes are required for decreasing sequences:

```R
seq(from = 9, to = 1, by=-2)
```
```
[1] 9 7 5 3 1
```

These round cases occur when the value of the `to` argument lies exactly in the sequence. In case this is not true, the `seq()` function will stop before the `to` argument is reached:

```R
seq(from = 9, to=2, by=-2)
```
```
[1] 9 7 5 3
```


### Varying sequence length 

When these three numbers define the sequence in a non-trivial way, it is difficult to foresee how many values there will be in the sequence - but we have a way to force the sequence to have a particular length with the `length.out` argument. This will break down the `from`-`to` interval to `length.out-1` equal intervals, leading to a vector with a length of `length.out`:

```R
seq(from = 9, to=2, length.out=5)
```
```
[1] 9.00 7.25 5.50 3.75 2.00
```

```R
# the difference between values
from <- 9
to <- 2
length.out <- 5
(from-to)/(length.out-1)
```
```
1.75
```

# Integer sequences - the colon (`:`) operator

Those tnteger sequences are the most frequently used form of this construct where the step size is exactly 1. We have a way to simplify this with the colon (`:`) operator. For instance, the following sequence:
```R
seq(20, 25)
```
```
[1] 20 21 22 23 24 25
```

can be written as

```R
20:25
```
```
[1] 20 21 22 23 24 25
```

This operator also works with negative values in all directions

```R
4:-2
```
```
[1] 4 3 2 1 0 -1 -2
```












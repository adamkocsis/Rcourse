---
parent: Vectorization 
layout: material 
nav_order: 4
title: Vectorized operations
topic: "vectorized_operations"
level: "2"
grand_parent: "Level 2 - Advanced Beginner"
---

# Vectorizing logical expressions

Consider the same set of numbers as earlier:

```R
numbers <- c(-4, 6, -3, 5, -2, 4, -1, 3)
```

and let's subset again for the positive numbers, which we can do like this:

```R
# this is the same as earlier
numbers[c(2,4,6,8)]
```

This works, but this is a stiff, rigid solution. If the vector changes, our solution will no longer work.

```R
numbers <- c(-10, -4, 6, -3, 5, -2, 4, -1, 3)

# The same expression leads to a totally different result
numbers[c(2,4,6,8)]
```
```
[1] -4 -3 -2 -1
```

For this reason it is a much better solution to express what we want as a **calculation** rather than **hard-coding** numbers into our code. This is a general principle and cannot be emphasized enough:

**Whenever it is possible, DO NOT HARD-CODE NUMBERS, TEXT OR DATA IN YOUR CODE. Period.**

For processing data, we write them into data files and read them in with dedicated functions. 

Rather than including numbers and data in your code, use calculations to get what you need.

# Positive numbers

For finding positive numbers in a vector, we have to describe what we want as a calculation. If we want to know whether a number `x` is positive, all we need to do is compare it to 0. 
```R
x>0
```

If `x` is larger then `0`, the result is `TRUE`, if it is lower, the result is `FALSE`.

We can use a simple iteration to repeat this test for every value in the vector.

```R
result <- NULL

# repeat for every number in the numbers vector
for(i in 1:length(numbers)){
	# the current number
	current <- numbers[i]
	
	if(current>0){
		result <- c(result, current)
	}
}

result
```
```
[1] 6 5 4 3
```

# Combined 

The solution above is easy, but it is a bit too complicated. 
We already know that we can use logical subscripts to extract parts of a vector - and we can actually use  the code above to create such a vector.

```R
result <- NULL

# repeat for every number in the numbers vector
for(i in 1:length(numbers)){
	# the current number
	current <- numbers[i]

	# the comparison with the current value - either true or false
	thisResult <- current>0

	# add to the rest
	result <- c(result, thisResult)
}
result
```
```
[1] FALSE  TRUE FALSE  TRUE FALSE  TRUE FALSE  TRUE
```

Then we can use this in getting the subset we want:

```
numbers[result]
```

Now we just have to find a way to make the code chunk to get this logical vector shorter.

# Vectorized equals

In every iteration that we do in the previous section we are comparing the vector's values to `0`. Similar to this table

| index | value | compare with | result  |
|-------|-------|--------------|---------|
| 1     | `-4`  | `0`          | `FALSE` |
| 2     | `6`   | `0`          | `TRUE`  |
| 3     | `-3`  | `0`          | `FALSE` |
| 4     | `5`   | `0`          | `TRUE`  |
| 5     | `-2`  | `0`          | `FALSE` |
| 6     | `4`   | `0`          | `TRUE`  |
| 7     | `-1`  | `0`          | `FALSE` |
| 8     | `3`   | `0`          | `TRUE`  |
	
	
Note that the column of zeros can be represented as:

```R
zeros <- c(0,0,0,0,0,0,0,0)
```

or as we have seen earlier, with

```R
zeros <- rep(0,8)
```

In R, such comparisons are vectorized automatically. You get the column on the right-hand side if you execute the comparison for every pair of values, like this:

```R
result <- NULL

for(i in 1:length(numbers)){
	# the comparison, now with two vectors 
	smallCalculation <- numbers[i] > zeros[i]
	result <- c(result, smallCalculation)
}
result
```
```
[1] FALSE  TRUE FALSE  TRUE FALSE  TRUE FALSE  TRUE
```

What you do is a pairwise comparison of values of the same index, which is very straightforward. This also can be used very frequently, so in R we actually notate it like this:

```R
numbers > zeros
```
```
[1] FALSE  TRUE FALSE  TRUE FALSE  TRUE FALSE  TRUE
```

Since both `numbers` and `zeros` are 1) vectors, and they 2) have the same length, the result of this calculation is going to be a vector of logical values, as before.

This effectively reduces our chunky for loop calculations to this:

```
numbers > rep(0, length(numbers))
```
```
[1] FALSE  TRUE FALSE  TRUE FALSE  TRUE FALSE  TRUE
```

And conveniently, finding the positive values in the vector becomes

```R
numbers[numbers > rep(0, length(numbers))]
```
```
[1] FALSE  TRUE FALSE  TRUE FALSE  TRUE FALSE  TRUE
```

But this can condensed even more... due to a handy feature, called **recycling**.

# Recycling with different lengths (general case)

But what happens when the length of the two vectors are not the same?

Consider this case: we omit one value from the set of numbers, e.g. the last:

```R
numbers2 <- numbers[-length(numbers)]
numbers2
```
```
[1] -4  6 -3  5 -2  4 -1
```

And we then do the comparison, **but using the original number of zeros**:

```R
numbers2 > rep(0, length(numbers))
```
```
[1] FALSE  TRUE FALSE  TRUE FALSE  TRUE FALSE FALSE  
Warning message:  
In numbers2 > rep(0, length(numbers)) :  
  longer object length is not a multiple of shorter object length`
```

We have 7 values in `numbers2`, so how come that we have 8 at the output? Why is the 8th value a `FALSE`?
And not only did we get this result, a warning pops up.

* * *

*Important: never ignore a warning. They are always there for a reason. Read them and try to avoid your script producing them!*

* * *

This is completely normal behavior, we just have to understand what is happening. But for that we might need another example, to trace the results better. Using the same idea for vectorized operations we can also add two vectors, for instance the original `numbers` vector and a sequence:

```R
numbers
```
```
[1] -4  6 -3  5 -2  4 -1  3
```

```R
sequence <- 1:length(numbers)
sequence
```
```
[1] 1 2 3 4 5 6 7 8
```

These two vectors are perfectly aligned, as in this table:


| numbers | sequence | operation | result |
|---------|----------|-----------|--------|
| `-4`    | 1        | `+`       | `-3`   |
| `6`     | 2        | `+`       | `8`    |
| `-3`    | 3        | `+`       | `0`    |
| `5 `    | 4        | `+`       | `9`    |
| `-2`    | 5        | `+`       | `3`    |
| `4`     | 6        | `+`       | `10`   |
| `-1`    | 7        | `+`       | `6`    |
| `3`     | 8        | `+`       | `11`   |

And indeed, this is what we get when we sum the two vectors together, element-by-element:

```R
numbers + sequence
```
```
[1] -3  8  0  9  3 10  6 11
```

If we again use `numbers2` instead, we get a similar warning as earlier:

```R
numbers2 + sequence
```
```
[1] -3  8  0  9  3 10  6  4
Warning message:  
In numbers2 + sequence :  
  longer object length is not a multiple of shorter object length  
```

But this time, we know a bit more... what is this at the end, where does this `4` come from?

The problem is illustrated in the table below:


| numbers2 | sequence | operation | result |
|----------|----------|-----------|--------|
| `-4`     | 1        | `+`       | `-3`   |
| `6`      | 2        | `+`       | `8`    |
| `-3`     | 3        | `+`       | `0`    |
| `5 `     | 4        | `+`       | `9`    |
| `-2`     | 5        | `+`       | `3`    |
| `4`      | 6        | `+`       | `10`   |
| `-1`     | 7        | `+`       | `6`    |
| **???**  | 8        | `+`       | `4`    |

By reversing the operation we can infer that the mistery value is in fact `-4` (`4-8 = -4`). 

You might already have a hunch of what is happening, but let's see what happens if repeat the same problem, but omitting another value from the end of the vector:

```R
numbers3 <- numbers2[-length(numbers2)]
numbers3
``` 
```
[1] -4  6 -3  5 -2  4
```

Adding this to our original `sequence` produces the same warning:

```R
numbers3 + sequence
```
```
[1] -3  8  0  9  3 10  3 14
Warning message:  
In numbers3 + sequence :  
  longer object length is not a multiple of shorter object length  
```

Now we have different mistery values at the end `3` and `14`. Let's look at our table to see what is happening.

| numbers3 | sequence | operation | result |
|----------|----------|-----------|--------|
| `-4`     | 1        | `+`       | `-3`   |
| `6`      | 2        | `+`       | `8`    |
| `-3`     | 3        | `+`       | `0`    |
| `5 `     | 4        | `+`       | `9`    |
| `-2`     | 5        | `+`       | `3`    |
| `4`      | 6        | `+`       | `10`   |
| **???**  | 7        | `+`       | `3`    |
| **???**  | 8        | `+`       | `14`   |


Using the same logic as before the original values were `3-7 = -4` and `14-8 = 6`, the same values that our `numbers2` vector starts with. 

| numbers3 | sequence | operation | result |
|----------|----------|-----------|--------|
| `-4`     | 1        | `+`       | `-3`   |
| `6`      | 2        | `+`       | `8`    |
| `-3`     | 3        | `+`       | `0`    |
| `5 `     | 4        | `+`       | `9`    |
| `-2`     | 5        | `+`       | `3`    |
| `4`      | 6        | `+`       | `10`   |
| **-4**   | 7        | `+`       | `3`    |
| **6**    | 8        | `+`       | `14`   |

What is happening here is that R notes that the two operands of the addition have different lengths, so R starts repeating the smaller vector, so we have something to execute our operation with. This behavior is called **recycling**.

# Recycling without a warning

Not all recycling cases produce warnings. For instance we can define this dummy vector here:

```R
dummy <- c(0, 1000)
```

and add it to our original `sequence` vector:

```R
sequence
```
```
[1] 1 2 3 4 5 6 7 8
```

Using the simple `+` operator:

```R
sequence + dummy
```
```
[1]    1 1002    3 1004    5 1006    7 1008
```

You probably guessed how this result emerges, by **recycling** the `dummy` vector as many times as needed.

| sequence | operation | dummy    | result |
|----------|-----------|----------|--------|
| 1        | `+`       | 0        | `1`    |
| 2        | `+`       | 1000     | `1002` |
| 3        | `+`       | **0**    | `3`    |
| 4        | `+`       | **1000** | `1004` |
| 5        | `+`       | **0**    | `5`    |
| 6        | `+`       | **1000** | `1006` |
| 7        | `+`       | **0**    | `7`    |
| 8        | `+`       | **1000** | `1008` |

The `dummy` vector is recycled exactly three times, leading to 8 values in total. Because the recycling can produce a vector that is exactly as long as the other one, without partial repetitions, this case **will not produce a warning**.

# Recycling of single values

This behavior is extremely useful - especially if consider that individual values are also vectors. This means that when we go back to the original problem of finding positive values in the `numbers` vector, where we had this 'concise' notation:

```R
numbers > rep(0, length(numbers))
```
```
[1] FALSE  TRUE FALSE  TRUE FALSE  TRUE FALSE  TRUE
```

we do not have to worry about replicating the zeros. We can just use a single value, and let it be recycled:

```R
numbers > 0
```
```
[1] FALSE  TRUE FALSE  TRUE FALSE  TRUE FALSE  TRUE
```

which leads to the same output. Accordingly, when we want to subset our vector to get the positive values, we can do it like this

```R
numbers[numbers > 0]
```
```
[1] 6 5 4 3
```

which looks beautifully simple. **THIS IS THE WAY how we were supposed to subset vectors in R using a logical expression.** 

# The rules of recycling are:

1. If you have a vectorized operation and the number of values in the two operands are not the same, you repeat the shorter vector, until you have as many values as in the longer.

2. If the length of the longer vector is not a multiple of the length of the shorter vector, the operation is still performed, but you get a warning. 

**This second case should be consciously avoided. In practice, in almost all cases it means that you are using an operation with two things that you did not intend to work with, i.e. a MISTAKE IN YOUR SCRIPT! Typos are excellent at producing such problems, which is why meaningful variable naming is so important.**








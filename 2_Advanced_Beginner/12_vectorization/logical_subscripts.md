---
parent: Vectorization 
layout: material 
nav_order: 3
title: "Logical subscripts" 
topic: "logical_subscripts"
level: "2"
grand_parent: "Level 2 - Advanced Beginner"
---

# Basic logical subscripts


Consider the same example as before. We have a set of numbers:

```R
numbers <- c(-4, 6, -3, 5, -2, 4, -1, 3)
```

If we want to get the same subset as earlier:

```R
numbers[c(2,4,6,8)]
```
```
[1] 6 5 4 3
```

Another way to extract a subset from this vector is via defining a logical vector, that indicates whatever we want to conserve from the vector. Whereever we want to keep a value, we indicate that by a `TRUE` value, and the everythign else should be `FALSE`: 

| index | value | keep?   |
|-------|-------|---------|
| 1     | `-4`  | `FALSE` |
| 2     | `6`   | `TRUE`  |
| 3     | `-3`  | `FALSE` |
| 4     | `5`   | `TRUE`  |
| 5     | `-2`  | `FALSE` |
| 6     | `4`   | `TRUE`  |
| 7     | `-1`  | `FALSE` |
| 8     | `3`   | `TRUE`  |

Let's define this vector:

```R
subs <- c(FALSE, TRUE, FALSE, TRUE, FALSE, TRUE, FALSE, TRUE)
```

The subsetting above can be programmed with a simple iteration. This is also an excellent way of introducing an extremely useful way to write `for()` loops. Instead of repeating a calculation directly on a vector, we will use the indices of the vector, which range from `1` to the length of the vector

```R
indices <- 1:length(subs)
indices
```
```
[1] 1 2 3 4 5 6 7 8
```

This is useful because we not only want to use the values of vector that we use to define the iteration (`subs`), but we also want to know how many iteration we have done, which is implicit in the `indices` vector.

```R
# the container to store the results
result <- NULL

# repeat for all values
for(i in indices){
	# The current logical value
	logic <- subs[i]

	# if this is TRUE, we keep the value, for which we can use if()
	if(logic){
		result <- c(result, numbers[i])
	}
}

# print out the result
result
```
```
[1] 6 5 4 3
```

In more condensed R code, this looks like this:

```R
numbers[subs]
```
```
[1] 6 5 4 3
```

This is a logical subscript, and it is extremely handy (also much faster than the for loop above).


# Logical subscript with missing values

The code above works only if there are no missing values in the `subs` subscript above.
But there can be cases when this happens. 

```R
subs2 <- subs
subs2[6] <- NA
subs2
```
```
[1] FALSE TRUE FALSE TRUE FALSE NA FALSE TRUE
```

Then using the same subscript form will lead to the injection of missing values:

```R
numbers[subs2]
```
```
[1] 6 5 NA 3
```

This behavior can be described with this bit of code:

```R
# the container to store the results
result <- NULL

# repeat for all values
for(i in indices){
	# The current logical value
	logic <- subs2[i]
	
	# if the current value is NA
	if(is.na(logic)){
		# insert it into the vector
		result <- c(result, NA)
	# if it is not, figure out whether we need to add something or not
	}else{
		# if this is TRUE, we keep the value, for which we can use if()
		if(logic){
			result <- c(result, numbers[i])
		}
	}
}
result
```
```
[1] 6 5 NA 3
```

# The `which()` function

We use such 'gappy' logical vectors very frequently - and in many cases these missing values are not needed. For this, there is a convenience function `which()`, which takes a single logical vector and turns it into a vector indices, telling us when that vector is `TRUE`.

```R
which(subs)
```
```
[1] 2 4 6 8
```

The function will ignore missing values:

```R
which(subs2)
```
```
[1] 2 4 8
```

This is equivalent with this chunk of code - but `which()` is much faster!

```
# the final container
result <- NULL

# iterate for all indices of subs2
for (i in 1:length(subs2)){

	# the current value
	current <- subs2[i]

	# only when it is not missing
	if(!is.na(current)){
		# if it is true, keep the indec
		if(current){
			result <- c(result, i)
		}
	}
}
result
```
```
[1] 2 4 8 
```


And conveniently get rid of the missing values, when we use a 'gappy' logical subscript:

```R
numbers[which(subs2)]
```
```
[1] 6 5 3
```


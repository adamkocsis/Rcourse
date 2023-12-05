---
parent: Randomness 
layout: material 
nav_order: 1
title: Shuffling and sampling
topic: "shuffle_sample"
level: "2"
grand_parent: "Level 2 - Advanced Beginner"
---

# Why?

The primary intended application of R (originally [S](https://en.wikipedia.org/wiki/S_(programming_language))) as a programming language is the implementation of statistical calculations. Many modern forms of statistics rely on explicit use of randomness, which forms the basis of simulations for inference, forward simulations and resampling statistics and some forms of machine learning. 

Creating actual random numbers is actually very difficult. In cases like simple programming, we use [pseudorandom number generation](https://en.wikipedia.org/wiki/Pseudorandom_number_generator) instead, which is good enough for our purposes, but can be predicted, when there is enough resources to analyse the patterns it generates. 

# Shuffling

The conceptually simplest implementation of random number generation is **shuffling**: taking a vector of values, and randomly reordering the elements. This is the primary use of the `sample()` function:

```R
# two 1s
a<- c(1, 1:6)
b <- sample(a)
b
```
```
[1] 3 1 6 4 5 1 2
```

Note that this result will be very likely different in your case! This is no mistake: the order should be randomized, every time the sample function is run, the result should be different.

```R
sample(a)
```
```
[1] 5 1 3 1 6 4 2
```


# Sampling (without replacement)

The process of **random sampling** involves the random selection of a subset of elements from a source that we call the **population**. In mathetmatical statistics, we typically deem the populations to have an infinite number of elements. The result of the sampling process is the **sample**.

The implemenation of sampling from a finite population (i.e. a vector of values) can be achieved if a second argument is given for the the `sample()` function. This second argument is the number of elements - which should be a non-negative integer value:

```R
sample(a, 4)
```
```
[1] 5 4 6 1
```

This is a random subset of the original vector - a sample. Note that none of the original elements can occur in this sample more times than in the original vector. This is the definition of sampling *without replacement*: whenever an element is selected from the population into the sample, the element is **removed** from the population. 

The vectorized implementation of this is simply the selection of the first 4 values of the shuffled vector, which is why we use the same function to shuffle and to sample:

```R
d <- sample(a)
d[1:4]
```
```
[1] 1 1 2 5
```

If you try to get a larger sample than the number of elements, you will get an error:

```R
sample(a, 8)
```
```
Error in sample.int(length(x), size, replace, prob) : 
  cannot take a sample larger than the population when 'replace = FALSE'
```


# Sampling - with replacement

There are contexts when we actually want execute sampling with a special twist: every time when we take out a single element, we put it back into the sample. This we can achieve by setting the `replace` argument from the default `FALSE` to `TRUE`.

```R
sample(a, replace=TRUE)
```
```
[1] 1 5 4 1 2 1 1
```

Note that this result contains more `1` values than there was in the original vector (You might need to run this several times to get a similar result). This implementation can be written with simple programming tools like this:

```R
# use the original sourc vector
pop <- a
# the number of desired elements
# as many as there originally was
n <- length(pop)

# sample
sam <- rep(NA, n)

# get every element, one-by-one
for(i in 1:n){
	# take one element from the original vector and save it
	sam[i] <- sample(a, 1)
}
sam
```
```
[1] 6 4 6 6 4 2 1
```


One of the benefits of *sampling with replacement* is that we can create as big a sample as we want: since the elements are put back into the vector, we can always sample them again:

```R
sample(a, 15, replace=TRUE)
```
```
[1] 3 5 3 1 1 3 3 1 3 5 3 2 4 4 3
```

Why is this any good? Because the frequency of the values (i.e. their distribution) will be approximately the same as that in the original vector, given that we create a large enough set - we will just have more values to work with, and with random samples. 


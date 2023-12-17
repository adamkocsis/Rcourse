---
parent: Randomness 
layout: material 
nav_order: 2
title: The r*dist* set of functions
topic: "r_dist"
level: "2"
grand_parent: "Level 2 - Advanced Beginner"
---

# Distributions

Statistics frequently utilize the concept of distributions that come from probability theory. These distribution represent infinite, continuous populations, that we can sample from.

Distributions are organized into **families**, which is a set of rules that describe the expected frequency of values. A specific distribution is given by a distribution family and its **parameters**. 


# The uniform distributions

For instance, one of the most frequently used distribution families is the [**uniform distribution** family](https://en.wikipedia.org/wiki/Continuous_uniform_distribution), which can be described with two **parameters**: a minimum (*a*) and a maximum (*b*). The uniform distribution expresses that if you would draw random numbers from the continuous interval between *a* and *b*, **every number - with the minimum and the maximum included - has exactly equal chance** of getting drawn. 

The simplest, and most important distribution in the uniform distribution family is the **standard uniform distribution**: *U*(0,1) - *U* represent the the distribution family, 0 and 1 are the parameters. 

> Note: Almost all implementations of (pseudo)random number generation are actually derived from this simple distribution!

# Sampling from the uniform distribution

We can sample from this distribution in R using the `runif()` function. The first argument of this function (`x`) sets the number of elements that we want to draw from this distribution. 


```R
# getting 5 values from U(0,1)
runif(5)
```
```
[1] 0.0001456398 0.9648580905 0.3221379726 0.3516660845 0.3109391942
```

Note that the results of this random draw will not be ordered, and every time you run the function, you will get a different result.


# Other uniform distributions

You can use the usual question mark `?runif` command to acces the manual file fo this function. If you look up the usage of the `runif()`, you will see that it actually allows you to set the minimum and maximum parameters, so you can generate random numbers from any other uniform distribution, by setting the `min` and `max` arguments.


```R
# getting 5 values from U(10,20)
runif(3, min=10, max=20)
```
```
[1] 19.87434 12.28877 17.62724
```

Note that this manual page is shared with other functions `dunif()`, `punif()`, `qunif()` that generate other descriptors of these distributions. You can guess that the '-unif' postfix indicates the uniform family. The r- prefix indicates random number generation. 


# Confirming results: large numbers

When only small samples are generated, they will be considerably uneven. However, you can quickly confirm the uniformity of this distributionif you create 1) a **large enough sample** and 2) make a **histogram** from it. 


```R
# getting one million values
bigSamp <- runif(1e6, min=10, max=20)
hist(bigSamp)
```
![]({{site.url}}{{site.baseurl}}/images/uniform_histogram.png)

# Other families

You can guess now that random number generation (and also the other distribution-functions) can be executed with other distributions as well! 

These include, for example, the following frequently used distribution families (both discrete and continuous):

| Family      | Random number generation |
|-------------|--------------------------|
| Uniform     | `runif()`                |
| Binomial    | `rbinom()`               |
| Normal      | `rnorm()`                |
| Geometric   | `rgeom()`                |
| Exponential | `rexp()`                 |
| Lognormal   | `rlnorm()`               |
| Beta        | `rbeta()`                |

See `?Distributions` for a complete list.





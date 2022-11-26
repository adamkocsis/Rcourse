---
parent: Iteration basics
layout: material 
nav_order: 2
title: Example application 
topic: "while_euler"
level: "2"
grand_parent: "Level 2 - Advanced Beginner"
---

# Estimating Euler's number

Iterations are insanely useful for mathematics. There are lots of problems that we can only solve with these, and there are also cases when we can reach to simpler solutions by using such methods.

For instance, think about this repetition, using either the previous `Fact()` function, or the implementation in base R: `factorial()`:

```R
estimate <- 1/factorial(0)
estimate <- estimate+1/factorial(1)
estimate <- estimate+1/factorial(2)
estimate <- estimate+1/factorial(3)
estimate <- estimate+1/factorial(4)
estimate <- estimate+1/factorial(5)
```

Factorials increase very-very fast, which means that their reciprocals decrease very-very fast as well. If you sum up the entire series of these reciprocals, you approach a constant value, *e*, [Euler's number](https://en.wikipedia.org/wiki/E_(mathematical_constant), one of the most important constants in mathematics.

This value is irrational, which also means that we cannot really use it in calculations with absolute precision, we can only use an approximate estimate. The precision that we want to use depends on the calculation and that will define the number of repetitions of the calculation above. Needless to say, we do not want to write out this repetition, we want to use iteration to get the precision that we want.

# Euler's number with while

This is actually rather easy with programming: we define the number of desired iterations (*n*), we count how many repeations we do, and then stop, when we are done.

```R
n <- 15

# initialization
count <- 0
estimate <- 0

# start iteration
while(count < 15){
	# the estimate
	estimate <- estimate + 1 / factorial(count)
	# loop counter increment
	count <- count + 1
}
estimate
```
```
[1] 2.718282
```

*Note that we here we initialize `count` with `0`, and we stop before we reach 15 (`<`). This way we get exactly 15 iterations.*

You can also add a line to print the value of `estimate` in every iteration. 

```R
<- 15

# initialization
count <- 0
estimate <- 0

# start iteration
while(count < 15){
	# the estimate
	estimate <- estimate + 1 / factorial(count)
	# display the estimate
	message(estimate)
	# loop counter increment
	count <- count + 1
}
estimate
```
```
1
2
2.5
2.66666666666667
2.70833333333333
2.71666666666667
2.71805555555556
2.71825396825397
2.71827876984127
2.71828152557319
2.71828180114638
2.71828182619849
2.71828182828617
2.71828182844676
2.71828182845823
```

Note that it is a bit difficult to see how this value changes from this kind of console print. For a more detailed assessment, we have to use a different kind of output. We either need to plot our results, or we have to save every value in an object. 



# Note about using `while()`

Although `while()` is a simple way to understand iteration, it might not necessarily be the best choice for writing loops. Since most iterative calculations are based on object structure (i.e. repeating things for every entity in a set), `for()` loops can be easier to comprehend, safer to control and easier to predict. However, there are some cases, when while loops are really necessary and better reflect the intention behind the iteration: when we want to repeat a calculation until a certain result is met, but we do not know how many times we actually need to repeat it. Under other circumstances, `for()` loops are usually better.



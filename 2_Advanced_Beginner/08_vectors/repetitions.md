---
parent: Vectors 
layout: material 
nav_order: 2
title: Replications
topic: "replications"
level: "2"
grand_parent: "Level 2 - Advanced Beginner"
---

# Replications (Repetitions)

Following the previous exercise, the simplest case of replication is when we want to repeat one value a number of times.

```R
# the thing you want to repeat
x <- "Slartibartfast" 
# the number of times you repeat it
times <- 4
# the starting values
count <- 1
result <- NULL
# repeat as long as needed
while(count <= times){
	# the final result
	result <- c(result, x)
	# increment counter
	count <- count + 1
}
result
```
```
[1] "Slartibartfast" "Slartibartfast" "Slartibartfast" "Slartibartfast"
```


# The `rep()` function

Replications are extremely common in R, and for this reason, there is a convenience function: `rep()`. Check out its help file with `?rep`!

In its basic form, `rep()` function takes at least two arguments: the thing you want to replicate (`x` - **can be of any type!**), and how many times you want to repeat it (`times`).

For instance, if you want to repeat the example above you only have to say, which is considerably shorter.

```R
rep("Slartibartfast",4)
```
```
[1] "Slartibartfast" "Slartibartfast" "Slartibartfast" "Slartibartfast"
```

# Repeating multiple values

Note that since the combine function (`c()`) can be used with multiple values, you can actually repeat entire vectors with the examples above (also with the `while` loop)!

```R
a <- c(1,100,1000)
rep(x=a, 3)
```
```
[1]    1  100 1000    1  100 1000    1  100 1000
```

repeating the vector `a` 3 times.

# More complex repetitions (later)

There are more complex ways to replicate a particular entity: these give you some of the examples, which we will see at a later point. 
- `rep(a, each=3)`
- `rep(a, c(3,2,1))`
- `rep(a, length.out=10)`

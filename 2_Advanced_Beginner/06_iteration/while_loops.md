---
parent: Iteration basics
layout: material 
nav_order: 1
title: Loops with <tt>while</tt> 
topic: "while_loops"
level: "2"
grand_parent: "Level 2 - Advanced Beginner"
---

# About iteration

Iteration is one of the primary reasons why computers are useful: to repeat tasks many times. 

Let's assume that you want to repeat the same commands multiple times, such as these messages:

```R
{
message("A message!")
message("A message2!")
message("A message!")
message("A message2!")
message("A message!")
message("A message2!")
message("A message!")
message("A message2!")
}
```

This manual way of repeating commands in extremely ineffective, as the number of programming statements have to match the number of repetitions. This is why loops were implemented: to make such automatic repetition short and easy.

# Syntax of `while()` loops

The simplest form of iteration is the `while()` loop. This structure is almost the same as that of `if()` statements. Compare the 'syntactic blueprint' of these two constructs:

```
if(<logical value>) <command/block>
while(<logical value>) <command/block>
```

The two are technically the same - but we need some tweaking to make this work for us. The idea is the same: if the value indside the parentheses is `TRUE`, the command/block will execute. In the case of `if`, the command executes exactly once. In the case of `while`, the commands will be repeated as long as the value in the parenthesis is `TRUE`. The simples case to illustrate the working of while is with the infinite loop.

### The infinite loop

The keyword is the only difference between the two constructs above. The following block of code is syntactically valid, but its utility if questionable. 



```R
while(TRUE){
  message("A message!")
  message("A message2!")
}
```

This is an infinite loop: R will continue to print these two messages, as long as you do not quit from the looping. In a terminal you can use Ctrl-C to quit from such an infinte loop. In RStudio, you should be able to break out from the infinite loop, by clicking on the red stop sign. 

*NOTE, if you are running RStudio: some distributions were not be able recover your R from this. If you are running R in a terminal, recovering from such cases is not a problem.*

The sequence of instructions:
1. Once R sees the `while()` keyword, it will evaluate whether the value in the parentheses is `TRUE` or `FALSE`. 
2. If the value is `TRUE`, then the block will execute.
3. After the block is executed, R will jump back to the line with the `while()` keyword.
4. Then R will repeat the steps 1-3, as long as the logical value is `TRUE`.

This is where the infinite loop is coming from: since nothing changes in the loop, there is no way for the condition to be `FALSE`, so the loop cannot quit.

### Changing the loop 

To make the `while()` construct much more useful, we need to change something in every iteration. Running this bit of code will still result in an infinite loop, but at least the loops will be somewhat different - as you can see if from the changing message. The most common way of changing a `while()` loop is to add a loop counter.

```R
count <- 1

while(TRUE){
  message(paste("message1", count))
  # increment
  count <- count + 1
}
```


### A closed `while()` loop

The simplest way to get out of a `while()` loop is to **make the condition dependent on the variable that you change in the loop**. The most common way of doing this is with a **logical operator**. 

```R
i <- 1

while(i<=4){
  message(i)
  
  # increment
  i = i + 1
}
```

```
1
2
3
4
```

In this case the counter (`i`) is incremented in every step, until the condition `i<=4` evaluates to `FALSE`. 

### Sequential execution

The simplest way to understand what exactly is happening in the code above is to run the code manually. 

First, the iterator is initialized:

```R
i <- 1
```

Then the `while()` keyword is encountered. R evaluates

```R
i<=4
```
```
TRUE
```

and since it is `TRUE`, the block is executed (sequentially, line-by-line). 

##### Iteration 1

First 

```R
message(i)
```
```
1
```

and then 

```R
i <- i + 1
```

increments `i` from `1` to `2`. Since this is the last code in the block, R will jump back to the `while()` keyword. It will re-evaluate the condition:

```R
i<=4
```

```
TRUE
```
which is still `TRUE`, because `2<=4` is `TRUE`. The code will execute again.

##### Iteration 2

```R
message(i)
```
```
2
```

```R
i <- i + 1
```
increments `i` from `2` to `3`. Since this is the last code in the block, R will jump back to the `while()` keyword.

```R
i<=4
```
is still 
```
TRUE
```
because
```
3<=4
```
The code will execute again.

##### Iteration 3

```R
message(i)
```
```
3
```

```R
i <- i + 1
```
increments `i` from `3` to `4`. Since this is the last code in the block, R will jump back to the `while()` keyword.

```R
i<=4
```
is still 
```
TRUE
```
because
```
4<=4
```
The code will execute again.


##### Iteration 4

```R
message(i)
```
```
4
```

```R
i <- i + 1
```
increments `i` from `4` to `5`. Since this is the last code in the block, R will jump back to the `while()` keyword.


###### End of the loop

```R
i<=4
```
is now  
```
FALSE
```
because
```
5<=4
```

R will exit the loop at this point. The code will continue with the lines after the block.

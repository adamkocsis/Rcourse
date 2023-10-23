---
parent: "Conditionals"
layout: material 
nav_order: 2
title: If and else statements 
topic: "if_and_else_statements"
level: "2"
grand_parent: "Level 2 - Advanced Beginner"
---

# Why?

So far we have looked at statements that were executed when a condition was fulfilled, but nothing happened when it was not:

```R
# input has to be number
input <- 12
if(input>=0) result <- "Awesome!"
message(result)
```

```
Awesome!
```

In this case, if we enter a negative value as `input`, then nothing at all will happen, which can have dire consequences: 


```R
# input has to be number
input <- -52
if(input>=0) resultNew <- "Awesome!"
message(resultNew)
```

```
Error: object 'resultNew' not found
```

This error occured because our workspace does not have a `resultNew` object - it would only be defined if the value of `input>=0` were `TRUE`, but it was `FALSE`.


To make this program work with `input` set to a negative value, we would have to provide a complimentary expression, that makes sure that the variable we define exists: 

```R
# input has to be number
input <- -52
if(input>=0) resultNew2 <- "Awesome!"
if(input<0) resultNew2 <- "Not great!"
message(resultNew2)
```

```
Not great!
```

Such complementary needs are very frequent in programming languages. To make them simpler, they are usually expressed with `if-else` paired statements.

```R
# input has to be number
input <- -52
if(input>=0) resultNew2 <- "Awesome!" else resultNew2 <- "Not bad!"
message(resultNew2)
```

```
Not bad!
```

In our case this chunk of code behaves exactly the same as the one above - but is also faster, and less error prone, as you only have to evaluate one logical expression: `input>=0`. Also note, that instead of two potential forking points, you have just one (with the double `if` case you actually have the ability to alter the value of `input`, and then the logical statements might not be complementary anymore!). 


The blueprint for this is the same as with simple `if` statments, but with the addition of the `else` keyword:

```
if(<logical value>) <commandWhenTRUE> else <commandWhenFALSE>
```

You can substitute the single commands with entire blocks (sets of statements between braces: `{}`). The following code is exactly the same as the one before.


```R
# input has to be number
input <- -52

if(input>=0){
	resultNew3 <- "Awesome!"
}else{
	resultNew3 <- "Ooh, even better!"
}
message(resultNew2)
```

```
Ooh, even better!
```


The use of `if-else` pairs is extremely common in R, usually more common then simple `if` statements.



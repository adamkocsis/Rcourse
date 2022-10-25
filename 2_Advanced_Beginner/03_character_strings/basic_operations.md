---
parent: "Character strings"
layout: material 
nav_order: 2
title: Basic operations 
topic: "basic_operations"
level: "2"
grand_parent: "Level 2 - Advanced Beginner"
---

# Basic operations with strings

### Number of characters in a string

The simples possible operation that we can do with character strings is to know how long they are. In R we do this with the `nchar()` function (**not `length()`**):

```R
one <- "R"
nchar(one)
```

```R
one <- "Really."
nchar(one)
```

### Concatanating characters into strings

Concatenation is the process of creating strings from individual characters or other strings. In R the `paste()` function is the workhorse for this operation. 

```R
first <- "Mr."
second <- "Nimbus"
paste(first, second)
```

The result is:

```
"Mr. Nimbus"
```

The function `paste()` accepts as many arguments as you like: 

```R
first <- "Mr."
second <- "Nimbus"
paste(first, first, first, second)
```

Note the space (`" "`) between the concatenated parts. This appears because the argument `sep` has this as the default value:

```R
first <- "Mr."
second <- "Nimbus"
paste(first, second, sep=" ")
```

This you can set to anything else, even entire words:

```R
first <- "Mr."
second <- "Nimbus"
paste(first, second, sep=" (nope) ")
```

Or nothing at all:


```R
first <- "Mr."
second <- "Nimbus"
paste(first, second, sep="")
```

This is exactly the behavior of variant of this function `paste0()`, which allows you to save writing out this argument:

```R
first <- "Mr."
second <- "Nimbus"
paste0(first, second)
```

### Printing to the console

R's console displays us feeback from the console. In case we want to force the printing of some information to the console, the nicest way of doing that is with the `message()` function, that wraps the information in a nice and clean way:

```R
message("This is a message.")
```

The `message()` function expects a **character string** as input argument. This is where the paste function can be extremely handy.


Note that we cannot do much with such messages (for now) - but they can be super informative for learning and to see the sate of our program.








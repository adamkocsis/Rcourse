---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults
title: Statements
layout: material 
nav_order: 1
parent: Material
has_children: true
---

# Programming statements

The R language is built with statements: the fundamental building blocks.

The interpreter will try to evaluate our instructions when a newline character is entered. 

The grammar of the language is frequently referred to as Syntax.

# Function calls

Functions are the "verbs" of the programming language, the instructions that we give to the computer: what to do. 

Every statement includes at least one function call: either explicitly or implicitly. Without a function call, the computer would not do anything. 

## Showing the content of objects
When you type the name of an object into the console, a special function called `show()` is called automatically. This prints out either the contents of an object, or shows some details that are necessary to understand the contents. 

```r
letters
```


```r
show(letters)
```


## Operators

We use various symbols in a programming language, some of them, such as `>`, `!`, `<-` are called **operators**. Operators are 'Syntactic sugar'.


## Explicit function calls

Explicit function calls are recognizable using the the `()` (parentheses) following the name of the function, for example:

```r
c()
mean()
x11()
```






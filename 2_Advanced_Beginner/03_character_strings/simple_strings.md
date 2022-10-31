---
parent: "Basic character strings" 
layout: material 
nav_order: 1
title: Simple strings 
topic: simple_strings 
level: "2"
grand_parent: "Level 2 - Advanced Beginner"
---

# About character strings

Formally a single **character** represents a single symbol. For instance, this is a single character between the double quotes:

```R
"R"
```


Luckily, R does not make a difference between single `'` and double `"` quotes, the interpreter will recognize this just as fine, and will immediately turn it to double quotes.

```R
'R'
```

The only thing that you need to be aware of is that you **cannot mix these up**. 

```R
"R' # !!! Not a complete expression
```

If you try to run this statement, then the interpreter will not consider this as a closed, complete expression. It will expect you to continue entering values, which is visible from the plus signs (`+`) at the beginning of the line, where the prompt should be.

![img]({{site.url}}{{site.baseurl}}/images/R_quote_console.png)

*If you ever see this unexpectedly, then you either need to complete the expression byentering the closing member of the symbol pair, or you can cancel this statement with the `ESC` key. (or `Ctrl`+`C` in a UNIX terminal)*

# Characters vs. Character strings

When you include multiple **characters** between the quotes, then you have a **string of characters** or **character strings**:

```R
"R is cool."
```

You can include anything between these without problems: including single quotes.

```R
"R is 'cheeky'."
```

You can also include double quotes, but for that you have to use the so-called **escape characters**, which we will cover at a later point. We will also cover **character vectors**, which are built using individual **character strings**, but first, let's examine what we can do with simple strings.









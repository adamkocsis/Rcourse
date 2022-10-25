---
layout: exercise 
nav_order: 1
title: Expanding R statements 
id: 2022-10-24a_expansion
parent: Exercise registry
---


## Instructions

Rewrite the expressions to multiple statements, so every expression will have exactly one assignment and one other calculation!

* * *

### Example

##### Exercise

```R
ex <- 6^(2-4)+7 
```

##### Solution

```R
r1 <- 2-4
r2 <- 6^r1
ex <- r2 + 7 
```

## Note

This boring exercise should help with working through the basic order operations (from maths) .

* * *

### A.

```R
a <- (87-12)*45 + 32/(12 %% 5) * 84
```

### B. 

```R
b <- (76 * 3) * 4^(1+4 * 2)
```

### C.

```R
c <- (78 * 43) +1 + (56 - 2)^-1 *4 * 3-1
```

### D.

```R
d <- 12 + ((4 * 4) + 1)^2 / 3
```

### E.

```R
e <- ( 13 + 1 )^2^(5 + 1) * 4
```

### F. 

```R
f <- (12 ^ 2 + 4) * ( (3*4^3) %% 7 )
```

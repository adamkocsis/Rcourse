---
layout: exercise 
nav_order: 1
title: Exercises with Boolean algebra 
id: 2022-10-24c_boolean_algebra
parent: Exercise registry
---


## Instructions

When we combine logical values in a complex way, working with logical operators can be quite challenging and they need some practice. Calculate these expressions using nothing else but your brains - **do not use the computer**!

* * *

### Example

The result of 

```R
TRUE | (TRUE & FALSE)
```

is `TRUE`.


* * *

### A

```R
TRUE & (TRUE & FALSE)
```

### A

```R
TRUE | (TRUE & FALSE)
```

### B
```R
!(TRUE | (TRUE | FALSE))
```

### C
```R
TRUE & !(FALSE | TRUE)
```

### D
```R
!TRUE & !FALSE
```

### E
```R
TRUE | xor(TRUE, TRUE)
```

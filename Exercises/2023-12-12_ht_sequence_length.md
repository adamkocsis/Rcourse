---
layout: exercise 
nav_order: 1
title: Longest same-results sequence of heads or tails 
id: 2023-12-12_ht_sequence_length
parent: Exercise registry
---

Consider this vector of coin toss results

```R
tosses <- c("H", "T", "H", "T", "H", "T", "T", "T", "H", "T")
tosses
```
```
[1] "H" "T" "H" "T" "H" "T" "T" "T" "H" "T"
```

## Instruction

Calculate the highest number of coin tosses when the result was the same in a sequence (either heads or tails). Implement a function that returns the length of this longest streak as a single integer value!


| name      | `LongestStreak()`               |
|-----------|---------------------------------|
| arguments | `x` : vector of heads and tails |
| return    | A single positive integer       |

>Test your function with the `tosses` object above (and your own). In this case, the result should be `3`!



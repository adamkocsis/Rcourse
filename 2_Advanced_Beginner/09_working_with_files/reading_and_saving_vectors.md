---
parent: Using Files 
layout: material 
nav_order: 1
title: Reading and Saving R objects
topic: "reading_and_saving_r_objects"
level: "2"
grand_parent: "Level 2 - Advanced Beginner"
---

# Writing R objects

The simplest way to store an existing object is with using the `saveRDS()` function. `saveRDS()` creates an R binary object which represents the previously exported object perfectly - but it cannot be read into barely any other program. However it is still very important since this way we can be absolutely sure that the internal structure of our data is conserved, and it is extremely efficient. 

We can use it to write an object to the harddrive like this:

```R
# an example vector
example <- c(1, 2, 3, 4, 5)
saveRDS(example, file="example.rds")
```

The standard file extension that we use for such binary files is `.rds`. 

Writing functions usually do not display anything on the console, which indicates that the writing has succeeded. However, the only way to make sure that the file writing was truly successful is via inspection. 


# Reading objects

The simplest way to inspect whether the file's was really saved appropriately is by trying to read the file back into R. 

The exported information from the previous section can be read in with the `readRDS()` function. 

```R
# Read in the previously written information
newExample <- readRDS(file="example.rds")
newExample
```
```
[1] 1 2 3 4 5
```












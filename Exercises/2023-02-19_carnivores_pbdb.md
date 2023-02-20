---
layout: exercise 
nav_order: 1
title: Carnivore genera in the Paleobiology Database
id: 2023-02-19_carnivores_pbdb
parent: Exercise registry
---


## Instructions

Calculate descriptive stats from the [Paleobiology Database](https://paleobiodb.org) (carnivores). 

1. Download this file: [carnivore_families.csv]({{site.url}}{{site.baseurl}}/download/carnivore_families.csv)

2. Read it into R with `read.csv()`! Check its structure and familiarize yourself with the columns. Every row represents one occurrence of a taxon in a collection. These usually belong to a species, but the fossils are sometimes not that easy to identifiy. For this reason we will look into the genera only. 

3. List the unique families in the table (column `family`). How many families are there? Do all names make sense?

4. This dataset, as most compiled data, needs some cleaning. We can make this set considerably better if we omit bad entries (ie. subset to that part, where column value is not equal to these). Write subsetting multiple commands to omit a. entries where the `family` is `""` (empty string); b. `family` is `"NO_FAMILY_SPECIFIED"`; c. `genus` is `""` (empty string)!

5. Subset your data to the family `"Canidae"`. Count the number of genera in this family! 

6. Make sure that the unique list of families do not contain the bad entries! Using a `for` loop, repeat step 5 and count the number of genera for every family!

7. Plot a histogram of the resulting vector!

8. Which family has the highest number of genera? What is the median number of genera in a family? 

9. Ensure that your script works without human intervention! Clean your code, close your R session, and repeat all calculations with the script that you wrote!

## Expected outputs

1. A named numeric vector:

`names`: names of families 
`values`: the number of genera in families

2. A histogram

3. The median of number of genera.

4. The name of the family that has th highest number of genera.

## Extra 

- Step 4 can be expressed in one line of code, can you write it like that? 
- Step 6 can be written without a for() loop. Do you know how to do it? 



 





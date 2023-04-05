---
layout: exercise 
nav_order: 1
title: Brachiopods in OBIS 
id: 2023-04-05_obis_brachiopods 
parent: Exercise registry
---


## Instructions

Calculate descriptive stats from the [Ocean Biodiversity Information System (OBIS)](https://obis.org/) (subset of brachiopod records). 

1. Download this file: [obis_brachiopoda.csv]({{site.url}}{{site.baseurl}}/download/obis_brachiopoda.csv)

2. Read it into R with `read.csv()`! Check its structure and familiarize yourself with the columns. Every row represents one occurrence of a taxon. These usually belong to a species, but sometimes they are higher-level entries.

3. List the unique genera in the table (column `genus`). How many genera are there? Do all names make sense? Omit all data rows where the `genus` column is empty quotes `""` 

4. We will be working with species-level information. Omit all data rows where the `species` column is empty quotes `""`!

5. Subset your data to the genus `"Lingula"`. List out the species names and count them. 

6. Plot a world map with the occurrences of *Lingula*! First, plot a world map with this chunk of code

```R
# plot a world map with this chunk
library(chronosphere)
ne <- fetch("NaturalEarth")
plot(ne, col="gray")
```

To make this work you have to install the `chronosphere` R extension package, which you can do with 

```R
install.packages("chronosphere")
```

Then you can plot the occurrences using the `points()` function, with the `decimallongitude` and `decimallatitude` columns as x and y coordinates, respectively. Set the arguments of `points()` so it draws red plus signs! 

7. Make sure that the unique list of genera (from *step 3.*) do not contain the entries that you omitted! Using a `for` loop count the number of species in every genus!

8. Make a histogram from the number of species in genera!

## Expected outputs

1. Species names in the genus *Lingula*. 

2. A world map with the occurrences of *Lingula*.

3. A named numeric vector with the number of species/genus:

`names`: names of genera 
`values`: the number of species in genera

4. A histogram


## Extra questions 

- Step 7 can be written without a `for` loop. Do you know how to do it? 



 





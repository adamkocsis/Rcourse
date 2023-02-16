---
layout: exercise 
nav_order: 1
title: Body mass of penguins in 2009
id: 2023-02-15_penguin_species
parent: Exercise registry
---


## Instructions

Calculate the median body mass of penguin species that were observed at the [Palmer station](https://allisonhorst.github.io/palmerpenguins/) in 2009.

1. Download this file: [penguins.csv]({{site.url}}{{site.baseurl}}/download/penguins.csv)

2. Read it into R with `read.csv()`! Check its structure and familiarize yourself with the columns. Every row represents one observed penguin. 

3. Subset the data to the the year 2009!

4. List the species that were observed this year (every species name occurs once)!

5. Select one species, e.g. the `Gentoo`, and subset the 2009 data to the corresponding part. Calculate the median body mass for this species. *Hint: missing values can be omitted if you use `median(x , na.rm=TRUE)` where x is the input vector to the function.*

6. Repeat step 5 with a `for()` loop, calculate the median mass of every species.

7. Plot a boxplot with adapting this code to your variable names (`yearDat` is the `data.frame` in my code):

```R
boxplot(body_mass_g ~ species, data=yearDat)
```

Check your results with this. The thick black horizontal lines should indicate the medians that you calculated earlier.

## Expected outputs

1. A named numeric vector:

`names`: names of species 
`values`: the median body mass of species

2. A boxplot 




 





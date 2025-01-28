---
layout: exercise 
nav_order: 1
title: IUCN Chameleon Data 
id: 2024-01-07_iucn_chameleon_table
parent: Exercise registry
---

![The IUCN Red List]({{site.url}}{{site.baseurl}}/images/1_en_nt_redlist_logo_iucnweb.jpg)


## Instructions

The [IUCN Red List](https://www.iucn.org/resources/conservation-tool/iucn-red-list-threatened-species) is an important resource in conservation biology. This body of data provides information on species distribution, taxonomy and conservation status. 

**1.** Download this file: [chameleons.csv]({{site.url}}{{site.baseurl}}/download/chameleons.csv). This includes some data from an older subset of this dataset (without the spatial data on the ranges themselves). 

**2.** Read it into R with `read.csv()`! Check its structure and ensure that the dataset has been read in correctly (remember to adjust the `sep` argument if necessary!). Every row should represent a range assessment of one species. There are multiple records of a species, when the species was assessed in multiple years. First, we need to know how many taxa there are in this dataset.

**3.** Create a subset of the `data.frame`, which has only the `"genus"` and `"binomial"` columns. Omit the duplicates! Use this subset for points **4.** and **5.**! 

**4.** How many chameleon species and genera are there in the dataset? *(two numbers, one for species, one for genera)*

**5.** Which genus has the highest number of species? *(character string)*

**6.** Using the original dataset, make a scatterplot using the `"SHAPE_Area"` and `"SHAPE_Leng"` variables (columns). These columns indicate the total area and length (maximum extent in one direction) of the species' distributions. Make a scatterplot of the two variables! Are the two variables correlated? *(a plot, and test)* 

**7.** For the remainder of the exercise, we need to omit duplicate entries for the species. We can do this by omitting every assessment record but the most recent one (timestamp is `yrcompiled` column), which can be implemented simply with:

```
# if your data.frame read in in point 2 is called 'chameleons'
chamReord <- chameleons[order(chameleons$binomial, chameleons$yrcompiled, decreasing=TRUE),]
chamFiltered <- chamReord[!duplicated(chamReord$binomial), ]
```

What is happening in this chunk of code? Make sure that you use these results for points 8 - 10!


**8.** The IUCN assigns species into categories of conservation status (see them [here](https://en.wikipedia.org/wiki/Conservation_status)). These assessments are in the `category` column. Create a subset for the **Vulnerable** `"VU"` category, and count the number of species in this category. Also calculate the median area (`SHAPE_Area`) for the category. (Using the `median()` function) *(two numbers, an integer and floating point number)*

**9.** Calculate the median shape area for all assessment categories! You can do this with a `for` loop that repeats the calculation in point **7** on every category in the dataset!  *(a numeric vector with categories in the names)*

**10.** Which category has the highest median geographic range? *(a category name, character string)*

## Extra challenge 

- Step 8 can be written without a `for` loop. Do you know how to do it? 
- Step 6 is an example of a beautiful power-law relationship between length and area. Make a [log-log](https://en.wikipedia.org/wiki/Log%E2%80%93log_plot) plot to show it! Can you construct a linear model with the logged data?



 





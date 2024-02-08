---
layout: exercise 
nav_order: 1
title: The mollusk subset of Sepkoski's compendium 
id: 2024-02-05_sepkoski-mollusk
parent: Exercise registry
---

![Sepkoski's compendium]({{site.url}}{{site.baseurl}}/images/JJSgenus.jpg)


J.J. Sepkoski's [compendium](https://strata.geology.wisc.edu/jack/) was the primary source of temporal distribution data for fossil taxa in the 1990s and the early 2000s. It includes taxonomic hierarchy information and stratigraphic range data (FAD and LAD) of many fossil genera. This legacy database has different versions that were circulating around when the [Paleobiology Database](https://paleobiodb.org/#/) was still in its infancy. 

We will use a subset of this database to look at the durations (the length of the total stratigraphic ranges) of mollusk genera. The hypothesis that we can use this results for is that **different mollusk classes have different average durations** - which translates to different overall pace of turnover. 

## Instructions

*The expected result of a step is indicated in italics at the end of the step.*

**1.** Download the compendium from here: [sepkoski_kiessling_processed.csv]({{site.url}}{{site.baseurl}}/download/sepkoski_kiessling_processed.csv). The one that this exercise uses is a copy processed by Wolfgang Kiessling and myself, and it has entries that match multiple updated timescales. 

**2.** Read in this file with `read.csv()` (remember to adjust the `sep` argument if necessary!)! Check its structure and ensure that the dataset has been read in correctly. (*a `data.frame` object*)

> Every row represents one genus. The taxonomy hiearchy is self-explanatory, but you will see lots of age assignments. For our exercise, we will use the ones based on the GTS 2020 timescale. The FADS for these are in the `bot95_ma` and the LADs are in the `top95_ma` column. Some rows will have missing value entries (`NA`) for these because the age assignment is not precise enough to resolve in this timescale. Nevertheless, we will use these throughout the exercise. 

**3.** Create a subset of the `data.frame`, for the phylum `"Mollusca"`! Make a character vector with all the **classes** that this phylum has in the database! How many different mollusk class entries are there?  *(a `character` vector, and a single `integer` value)* 

**4.** There is one class entry in this subset, which is not a proper class name (there are some more with questions marks!). Get rid of the data from this 'class', filter out the row(s) that belong to this entry and create an updated version of the mollusk subset! Again, list out the different class names and save them in a vector! *(a `data.frame`, and a `character` vector)*

**5.** Calculate the mean **duration** of all **Bivalve** genera (the rows that are in class `Bivalvia`) in the dataset! *(`numeric` value)*   
You can do this by following these steps:  
- **5a.** You get durations as the result of subtracting the FAD date from he LAD date, which you can then save into a new column. If you have the mollusk subset assigned to the `moll` name, then the durations will be `moll$duration <- moll$bot95_ma - moll$top95_ma`.  
- **5b.** Subset your data to the bivalves!  
- **5c.** Calculate the mean duration from these! (ignore the missing values (`NA`) - if you don't remember how, look at the help page of of the `mean()` function!)   

**6.** Using the result of **5b.** make a histogram from the durations of the bivalve genera! What can you say about this distribution? (*a histogram plot, some text description*)

**7.** Calculate the mean duration for all mollusk classes! You can do this with a `for` loop that repeats the calculation in points **5b** and **5c** on every class in the dataset (which you should have as a result of step **4**)!  *(a `numeric` vector with class names in the `names` attribute)*

**8.** Which class has the longest mean duration? *(`character` string)*





 





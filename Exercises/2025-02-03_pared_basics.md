---
layout: exercise 
nav_order: 1
title: The PaleoReefs Database 
id: 2025-02-03_pared_basics
parent: Exercise registry
---

![The PaleoReefs Database]({{site.url}}{{site.baseurl}}/images/paleoreefs.png)


The [Paleoreefs Database](https://www.paleo-reefs.pal.uni-erlangen.de/) is the foremost data source that allows us to analyze the evolutionary history of reef systems. This data source, compiled primarily by Wolfgang Kiessling, includes spatiotemporal distribution records of ancient reef sites, as well as some of their stratigraphical, physical and compositional properties.

Youi will use a subset of this database to look at the main reef builders and the latitudinal patterns of coral reef distribution. 

## Instructions

*The expected result of a step is indicated in italics at the end of the step.*

**1.** Download the publicly available subset of the database from here: [pared_public.csv]({{site.url}}{{site.baseurl}}/download/pared_public.csv). This subset has only a fraction of the variables from the complete database, but should be good enough for basic analyses. Make sure to put all files relevant to the exercise in a single project directory!

**2.** Read in this file with `read.csv()` (remember to adjust the `sep` argument if necessary!)! Check its structure and ensure that the dataset has been read in correctly. (*a `data.frame` object*)

> Every row represents one reef site, that has a name (`NAME`), formation (`FORMATION`) and some stratigraphic data (`SYSTEM`, `SERIES`, `INTERVAL`). The present-day geographical coordinates are in the `LON` and `LAT` columns. Reconstructed paleocoordinates (where the reefs were present in the past based on the PALEOMAP tectonic model) are in the `PALEO-LAT` and `PALEO-LON` columns. 

**3.** Where are these ancient reef sites today? Plot the distribution of reef occurrences on a present-day map! You can do this in any way you like - if you do not have a better idea, you can use NaturalEarth polygons from the chronosphere package as have done it earlier:

```r
# if you need to install something
# install.packages(c("chronosphere", "sf"))
library(chronosphere)
ne <- chronosphere::fetch("NaturalEarth", verbose=FALSE)
plot(ne$geometry, col="gray", border=NA)
```

*The result will be a single plot with occurrence points on it.*

**4.** Tabulate the number of reef sites per country! How many countries have reef records? Which country has the highest number of ancient reef sites? (a *numeric* and a *character* value)

**5.** Create a subset for the Cambrian system! In this subset, what were the main reef builder groups? Which entry occurs most frequently? (*character vector* and a single *character* value - there some entries that are not given!)

**6.** Create a subset of the overall reef dataset for those reefs where the main reef builders (column `BIOTA.MAIN`) are `Corals`! Use this subset for the subsequent analyses!

> Temperature has a huge effect on the latitudinal distribution of coral reefs. We know that climate has been much warmer in the mesozoic, and it has been getting cooler for the past couple dozen millions of years. This means that coral reef sites should draw nearer to the equator in general (e.g. their paleolatitude should be decreasing). To assess this, we have to calculate how far away from the equator we find reef sites (at their past geographic positions). To get an average of this, we can use to the absolute values of the latitudes (which mirrors the southern hemisphere, negative latitude values to the northern hemisphere), and we can calculate their median, and analyze how this changes through time.

**7.** Make a subset of the overall coral dataset, that come from the `"Jurassic"` system! How many coral reef sites are there? In this subset, calculate the median of the absolute **paleolatitude** of the reef sites! (a two *numeric* values)

**8.** Using a for loop, repeat step 7 for all systems in the dataset, so we know the median absolute paleolatitude of reef sites in all systems! (*named numeric vector*). 

**9** Unfortunately there is no numeric age data in this download, but we do want to order these results from older to younger systems. You know the correct order of these systems, right? You can use character subscripts, to do this ordering manually, like in this example:

```r
vec<- 1:5
names(vec) <- c("e", "d", "a", "c", "b")

# the correct order of values is then
vec[c("a", "b", "c", "d", "e")]
```

Once you have reordered the vector (e.g. `reordered`), you can visualize the order with:


```r
plot(reordered, type="o", axes=FALSE)
axis(1, at=1:length(reordered), label=names(reordered))
axis(2)
```

Do we see a support for our hypothesis? Have reefs been getting closer to equator in general?

> This of course can be studied at a higher resolution to see finer changes, but the general trend will be the same.





 





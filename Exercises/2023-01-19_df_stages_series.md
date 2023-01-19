---
layout: exercise 
nav_order: 1
title: Number epochs in geological periods
id: 2023-01-19_df_stages_series
parent: Exercise registry
---


## Instructions

Calculate the number of series/epochs in all Phanerozoic geological systems/periods! Here are the steps that need to be taken:

1. Download this file: [stages.csv]({{site.url}}{{site.baseurl}}/download/stages.csv)

2. Read it into R with `read.csv()`!

3. Subset to the Phanerozoic!

4. Select one system/period, e.g. the `"Jurassic"`, and subset the table to the corresponding part. Count how many different series/epochs there was in it. (`length(unique())`) 

5. Get a complete list of different systems/periods, which should be a vector, where every item occurs only once. 

6. Repeat step 4 with a `for()` loop, calculate the number of epochs in every period.

7. Assign names to the values.

+1. Use the combination of column subsetting, `unique()` and `table()` to get the same result (steps 4-7) without writing a loop. 

## Expected output

A named numeric vector:

names: periods/systems
values: the number of series/epochs in every period.


 





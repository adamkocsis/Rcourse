---
layout: exercise 
nav_order: 1
title: Counting the occurrences of <i>Favia</i>
id: 2023-01-17_favia-occurrencecount
parent: Exercise registry
---


![favia_favus]({{site.url}}{{site.baseurl}}/images/favia_favus.jpg)

*Favia favus*


## Instructions

Calculate the number of occurrences and collections of the genus *Favia* in this old excerpt from the [Paleobiology Database](www.paleobiodb.org).
1. Download the occurrence file: [favia.csv]({{site.url}}{{site.baseurl}}/download/favia.csv)

2. Read it into R with `read.csv()`!

3. Calculate how many occurrences (rows in the table) the genus has where the `stg` (stage) column's value is 87! This indicates Priabonian (Eocene) stage. This should be a single numeric value.

4. Calculate how many different collections (entries in the `collection_no` column) there are in this stage! This should be a single numeric value.

5. Calculate which `stg` numbers does this genus occurs! This should be a numeric vector.

6. Calculate the number of occurrences and collections in every stage! These should be two numeric vectors.

*Hint: initially, use a `for` loop to do this - although we will solve this in more functional way too!*






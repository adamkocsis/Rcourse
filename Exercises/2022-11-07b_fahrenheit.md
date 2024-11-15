---
layout: exercise 
nav_order: 1
title: Fahrenheit to Celsius Calculator
id: 2022-11-07b_fahrenheit
parent: Exercise registry
---

## Instructions

Based on an [other exercise]({{site.url}}{{site.baseurl}}/Exercises/2022-11-06a_definition_correction.html) (do that if you haven't yet), implement a function to calculate Celsius (°C)  values from Fahrenheit (°F)!

| what        | name                  |
|-------------|-----------------------|
| name        | FahrenheitToCelsius() |
| argument(s) | fahrenheit            |
| return      | single numeric value  |

## Testing

If you have worked correctly, then the following lines of code should be returning `TRUE`!

```R
# valid input
FahrenheitToCelsius(32) == 0
FahrenheitToCelsius(212) == 100

# input
is.na(FahrenheitToCelsius("asd"))
```





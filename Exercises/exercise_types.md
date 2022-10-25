---
title: Types of exercises
layout: default
nav_order: 1
parent: Exercises
permalink: Exercises/types_of_exercises/
---

# Types of exercises

{% for type in site.data.exercise_types %}

<div markdown="1">

## {{type.name}}

{{type.definition}}

{{type.short}}

</div>

{% endfor %}










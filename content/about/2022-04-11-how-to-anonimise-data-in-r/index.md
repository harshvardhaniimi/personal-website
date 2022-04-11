---
title: How to Anonimise Data in R?
subtitle: Function to Anonimise Names without Losing Details
author: Harshvardhan
date: '2022-04-11'
slug: how-to-anonimise-data-in-r
categories:
  - R
  - statistics
tags: []
draft: true
---

When writing dataset papers --- or for a hundred different reasons --- we sometimes want to anonimise our data. We have the information but we want to disguise it with certain keywords. In this blog, I am going to show how do it with R functions.

Unlike Ctrl + F and replace, this method is more reliable and sustainable. You have better command over what gets changed and how.

# Loading Packages


```r
# Loading Libraries
library(tidyverse)
```

```
## ── Attaching packages ─────────────────────────────────────── tidyverse 1.3.1 ──
```

```
## ✓ ggplot2 3.3.5          ✓ purrr   0.3.4     
## ✓ tibble  3.1.6          ✓ dplyr   1.0.8.9000
## ✓ tidyr   1.2.0          ✓ stringr 1.4.0     
## ✓ readr   2.1.2          ✓ forcats 0.5.1
```

```
## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
## x dplyr::filter() masks stats::filter()
## x dplyr::lag()    masks stats::lag()
```

```r
library(lubridate)
```

```
## 
## Attaching package: 'lubridate'
```

```
## The following objects are masked from 'package:base':
## 
##     date, intersect, setdiff, union
```

```r
library(stringr)
library(readxl)
library(tidylog)
```

```
## 
## Attaching package: 'tidylog'
```

```
## The following objects are masked from 'package:dplyr':
## 
##     add_count, add_tally, anti_join, count, distinct, distinct_all,
##     distinct_at, distinct_if, filter, filter_all, filter_at, filter_if,
##     full_join, group_by, group_by_all, group_by_at, group_by_if,
##     inner_join, left_join, mutate, mutate_all, mutate_at, mutate_if,
##     relocate, rename, rename_all, rename_at, rename_if, rename_with,
##     right_join, sample_frac, sample_n, select, select_all, select_at,
##     select_if, semi_join, slice, slice_head, slice_max, slice_min,
##     slice_sample, slice_tail, summarise, summarise_all, summarise_at,
##     summarise_if, summarize, summarize_all, summarize_at, summarize_if,
##     tally, top_frac, top_n, transmute, transmute_all, transmute_at,
##     transmute_if, ungroup
```

```
## The following objects are masked from 'package:tidyr':
## 
##     drop_na, fill, gather, pivot_longer, pivot_wider, replace_na,
##     spread, uncount
```

```
## The following object is masked from 'package:stats':
## 
##     filter
```


---
title: Number of PhDs
author: Harshvardhan
date: '2022-02-20'
slug: number-of-phds
categories:
  - R
  - statistics
  - economics
  - thoughts
tags: []
draft: true
---

Yesterday I was talking to one of my friends about his plans post PhD. "I want to go for pure sciences and abstract mathematics, but there are hardly any positions in academia on these topics.", he said. It got me into thinking how many PhD students graduate every year and if the demand (in academia or in industry) is less than that. But I didn't even know how many PhDs are awarded each year, let alone employed.

While searching for a dataset for my Text Mining class project, I discovered this dataset on number of PhDs by field. So, let's explore!

## Exploration


```r
library(tidyverse)
```

```
## ── Attaching packages ─────────────────────────────────────── tidyverse 1.3.1 ──
```

```
## ✓ ggplot2 3.3.5          ✓ purrr   0.3.4     
## ✓ tibble  3.1.6          ✓ dplyr   1.0.7.9000
## ✓ tidyr   1.1.4          ✓ stringr 1.4.0     
## ✓ readr   2.0.2          ✓ forcats 0.5.1
```

```
## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
## x dplyr::filter() masks stats::filter()
## x dplyr::lag()    masks stats::lag()
```

```r
# Using my personal theme
theme_h = function(base_size = 14) {
  theme_bw(base_size = base_size) %+replace%
    theme(
      # Specify plot title
      plot.title = element_text(size = rel(1), face = "bold", margin = margin(0,0,5,0), hjust = 0),
      # Specifying grid and border
      panel.grid.minor = element_blank(),
      panel.border = element_blank(),
      # Specidy axis details
      axis.title = element_text(size = rel(0.85), face = "bold", family="serif"),
      axis.text = element_text(size = rel(0.70), family="serif"),
      axis.line = element_line(color = "black", arrow = arrow(length = unit(0.3, "lines"), type = "closed")),
      # Specify legend details
      legend.title = element_text(size = rel(0.85), face = "bold"),
      legend.text = element_text(size = rel(0.70), face = "bold", family="serif"),
      legend.key = element_rect(fill = "transparent", colour = NA),
      legend.key.size = unit(1.5, "lines"),
      legend.background = element_rect(fill = "transparent", colour = NA),
      # Remove default background
      strip.background = element_rect(fill = "#17252D", color = "#17252D"),
      strip.text = element_text(size = rel(0.85), face = "bold", color = "white", margin = margin(5,0,5,0))
    )
}

theme_set(theme_h())
```


```r
# Loading dataset from their repository
phds = readr::read_csv("https://raw.githubusercontent.com/rfordatascience/tidytuesday/master/data/2019/2019-02-19/phd_by_field.csv")
```

```
## Rows: 3370 Columns: 5
## ── Column specification ────────────────────────────────────────────────────────
## Delimiter: ","
## chr (3): broad_field, major_field, field
## dbl (2): year, n_phds
## 
## ℹ Use `spec()` to retrieve the full column specification for this data.
## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.
```

```r
phds
```

```
## # A tibble: 3,370 × 5
##    broad_field   major_field                                 field   year n_phds
##    <chr>         <chr>                                       <chr>  <dbl>  <dbl>
##  1 Life sciences Agricultural sciences and natural resources Agric…  2008    111
##  2 Life sciences Agricultural sciences and natural resources Agric…  2008     28
##  3 Life sciences Agricultural sciences and natural resources Agric…  2008      3
##  4 Life sciences Agricultural sciences and natural resources Agron…  2008     68
##  5 Life sciences Agricultural sciences and natural resources Anima…  2008     41
##  6 Life sciences Agricultural sciences and natural resources Anima…  2008     18
##  7 Life sciences Agricultural sciences and natural resources Anima…  2008     77
##  8 Life sciences Agricultural sciences and natural resources Envir…  2008    182
##  9 Life sciences Agricultural sciences and natural resources Fishi…  2008     52
## 10 Life sciences Agricultural sciences and natural resources Food …  2008     96
## # … with 3,360 more rows
```

There are many records by fields --- in three levels of granularity. The column `year` tells about the year and `n_phds` is the number of graduates that year. Let's check the number of records we have for each year; it will also tell me range of data.


```r
phds %>% 
  count(year)
```

```
## # A tibble: 10 × 2
##     year     n
##    <dbl> <int>
##  1  2008   337
##  2  2009   337
##  3  2010   337
##  4  2011   337
##  5  2012   337
##  6  2013   337
##  7  2014   337
##  8  2015   337
##  9  2016   337
## 10  2017   337
```

There are 337 fields and we have records for each of them between 2008 to 2017. Let's see how many people are from which field.

### Number of PhDs by their Broad Field


```r
phds %>% 
  group_by(broad_field) %>% 
  summarise(n_phds = sum(n_phds, na.rm = T)) %>% 
  arrange(desc(n_phds))
```

```
## # A tibble: 7 × 2
##   broad_field                       n_phds
##   <chr>                              <dbl>
## 1 Life sciences                     205703
## 2 Psychology and social sciences    119116
## 3 Humanities and arts                53045
## 4 Education                          52639
## 5 Mathematics and computer sciences  35481
## 6 Other                              28855
## 7 Engineering                        18139
```

Here's what we observe.

**Life sciences** has most number of graduates. **Engineering** has least number of graduates --- even less than mysterious **Other**. I am interested in learning more about life sciences.


```r
phds %>% 
  filter(broad_field == "Life sciences") %>% 
  group_by(major_field) %>% 
  summarise(n_phds = sum(n_phds, na.rm = T)) %>% 
  arrange(desc(n_phds))
```

```
## # A tibble: 6 × 2
##   major_field                                           n_phds
##   <chr>                                                  <dbl>
## 1 Biological and biomedical sciences                     85637
## 2 Physics and astronomy                                  41176
## 3 Chemistry                                              25015
## 4 Health sciences                                        20882
## 5 Geosciences, atmospheric sciences, and ocean sciences  19868
## 6 Agricultural sciences and natural resources            13125
```

**Biological and biomedical sciences** has the most number of graduates. I thought chemistry would be part of engineering but I guess chemical engineering is different from engineering. Let me explore engineering too.


```r
phds %>% 
  filter(broad_field == "Engineering") %>% 
  group_by(major_field) %>% 
  summarise(n_phds = sum(n_phds, na.rm = T)) %>% 
  arrange(desc(n_phds))
```

```
## # A tibble: 1 × 2
##   major_field       n_phds
##   <chr>              <dbl>
## 1 Other engineering  18139
```

Oh, so no information. I guess I'll have to group by field.


```r
phds %>% 
  filter(broad_field == "Engineering") %>% 
  group_by(field) %>% 
  summarise(n_phds = sum(n_phds, na.rm = T)) %>% 
  arrange(desc(n_phds))
```

```
## # A tibble: 23 × 2
##    field                                            n_phds
##    <chr>                                             <dbl>
##  1 Computer engineering                               4030
##  2 Environmental, environmental health engineeringl   2001
##  3 Engineering, other                                 1488
##  4 Nuclear engineering                                1166
##  5 Operations research (engineering)                   985
##  6 Systems engineering                                 924
##  7 Petroleum engineering                               760
##  8 Structural engineering                              743
##  9 Agricultural engineering                            674
## 10 Polymer, plastics engineering                       658
## # … with 13 more rows
```

Now it's getting familiar again. Computer science leads it all. Let's visualise the counts.


```r
phds %>% 
  filter(broad_field == "Engineering") %>% 
  group_by(field) %>% 
  summarise(n_phds = sum(n_phds, na.rm = T)) %>% 
  ggplot(aes(reorder(field, n_phds), n_phds)) +
  geom_col() +
  coord_flip() +
  labs(y = "Number of PhDs", x = "Field (Engineering only)")
```

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-8-1.png" width="672" />

The data gives me opportunity to see how it grew up with the rise in popoularity of computer science. I've heard numerous time that its popularity has increased over the years. Let's check it via spiral plot.


```r
# Install the package first
# install.packages("spiralize")

# Load the library
library(spiralize)
```

```
## Loading required package: grid
```

```
## ========================================
## spiralize version 1.0.5
## Github page: https://github.com/jokergoo/spiralize
## CRAN page: https://CRAN.R-project.org/package=spiralize
## 
## If you use it in published research, please cite:
## Gu, Z. spiralize: an R package for Visualizing Data on Spirals. 
##   Bioinformatics 2021.
## 
## This message can be suppressed by:
##   suppressPackageStartupMessages(library(spiralize))
## ========================================
```

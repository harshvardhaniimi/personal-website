---
title: Notes on R
subtitle: Functions et al
summary: Functions et al
author: Harshvardhan
date: '2022-02-03'
slug: notes-on-r
categories:
  - R
tags: []
---

On one fine day when I have enough time, they'll all be wrapped into a package hosted on my Github. Until then, this page in their home.


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

## Show in Excel


```r
show_in_excel = function(.data)
{
   temp = paste0(tempfile(), ".csv")
   write.csv(.data, temp)
   fs::file_show(path = temp)
}
```

This can be used with pipes too.


```r
iris %>% 
  show_in_excel()
```

## Convert Missing Values to Zero

This function converts missing values in a vector to zero.


```r
n2z = function(x)
{
   x = ifelse(is.na(x), 0, x)
   return(x)
}
```

## Finding Index of Missing Elements

This function returns index of elements which are missing. Very useful in finding what observations are missing.


```r
which.na = function(x)
{
   return(which(is.na(x)))
}
```

## Removing Rows Based on Missing Values in a Column

Sometimes, I do not want to `na.omit()` because it will treat all features equally. I want to check values only for one column.


```r
na.rm.feature = function(x, colname)
{
   nas = which(is.na(x[,colname]))
   x = x[-nas, ]
   return(x)
}
```

## Find row where a condition is satisfied

This function can find observations that satisfy a condition. Typically, they are useful in finding specific elements. It is kind of a wrapper around dplyr's `filter()`.


```r
which.this = function(df, x)
{
  df %>% 
    filter(eval(parse(text = x)))
}
```

#### Example


```r
which.this(iris, "Sepal.Length > 6.5") %>% 
  head()
```

```
##   Sepal.Length Sepal.Width Petal.Length Petal.Width    Species
## 1          7.0         3.2          4.7         1.4 versicolor
## 2          6.9         3.1          4.9         1.5 versicolor
## 3          6.6         2.9          4.6         1.3 versicolor
## 4          6.7         3.1          4.4         1.4 versicolor
## 5          6.6         3.0          4.4         1.4 versicolor
## 6          6.8         2.8          4.8         1.4 versicolor
```

## Remove commas, dollars, or any other such characters

The code below replaces all commas with nothing.


```r
x = "300,000"
x = gsub(",", "", x)
print(x)
```

```
## [1] "300000"
```

## GGPlot2 Theme

See [official guide](https://ggplot2.tidyverse.org/reference/theme.html) for more details. Also see [Benjamin's blog](https://benjaminlouis-stat.fr/en/blog/2020-05-21-astuces-ggplot-rmarkdown/).

The default plot looks like this.


```r
iris %>% 
  ggplot(aes(x = Sepal.Length, y = Sepal.Width, colour = Species)) +
  geom_point() +
  labs(title = "Without my theme")
```

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-10-1.png" width="672" />

Once I run and set my theme, its way prettier.


```r
theme_h = function(base_size = 14) {
  theme_bw(base_size = base_size) %+replace%
    theme(
      # Specify plot title
      plot.title = element_text(
        size = rel(1),
        face = "bold",
        family = "serif",
        margin = margin(0, 0, 5, 0),
        hjust = 0
      ),
      # Specifying grid and border
      panel.grid.minor = element_blank(),
      panel.border = element_blank(),
      # Specidy axis details
      axis.title = element_text(
        size = rel(0.85),
        face = "bold",
        family = "serif"
      ),
      axis.text = element_text(size = rel(0.70), family = "serif"),
      axis.line = element_line(
        color = "black",
        arrow = arrow(length = unit(0.3, "lines"),
                      type = "closed")
      ),
      # Specify legend details
      legend.title = element_text(
        size = rel(0.85),
        face = "bold",
        family = "serif"
      ),
      legend.text = element_text(
        size = rel(0.70),
        face = "bold",
        family = "serif"
      ),
      legend.key = element_rect(fill = "transparent", colour = NA),
      legend.key.size = unit(1.5, "lines"),
      legend.background = element_rect(fill = "transparent", colour = NA),
      # Remove default background
      strip.background = element_rect(fill = "#17252D", color = "#17252D"),
      strip.text = element_text(
        size = rel(0.85),
        face = "bold",
        family = "serif",
        color = "white",
        margin = margin(5, 0, 5, 0)
      )
    )
}

theme_set(theme_h())
```


```r
iris %>% 
  ggplot(aes(x = Sepal.Length, y = Sepal.Width, colour = Species)) +
  geom_point() +
  labs(title = "With my theme")
```

<img src="{{< blogdown/postref >}}index_files/figure-html/unnamed-chunk-12-1.png" width="672" />

I like the arrowed axes and serif fonts.

## Better Quality Images in R Markdown

Using `.svg` as the image output format gives much better graphics quality than the default option. To use that, include the following code in R Markdown. [Source](https://stackoverflow.com/questions/64602680/how-to-set-svg-as-default-rendering-in-rmarkdown).


```r
knitr::opts_chunk$set(dev = 'svg') # set output device to svg
```

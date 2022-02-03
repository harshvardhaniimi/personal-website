---
title: Some R Functions et al
subtitle: Notes on R that are statistically significant 
summary: Notes on R that are statistically significant 
author: Harshvardhan
date: '2022-02-03'
slug: some-r-functions
categories:
  - R
tags: []
---

## Show in Excel

This function opens the data frame in Excel. Original credits to [Bruno Rodrigues](https://twitter.com/brodriguesco/status/1447468259725434886?s=20&t=CfH_SqI_DExZBaLKuSvZxA).

```
show_in_excel = function(.data)
{
   temp = paste0(tempfile(), ".csv")
   write.csv(.data, temp)
   fs::file_show(path = temp)
}
```

This can be used with pipes.

```
iris %>% 
  show_in_excel()
```

## Convert Missing Values to Zero

This function converts missing values in a vector to zero.

```
n2z = function(x)
{
   x = ifelse(is.na(x), 0, x)
   return(x)
}
```

## Finding Index of Missing Elements

This function returns index of elements which are missing. Very useful in finding what observations are missing.

```
which.na = function(x)
{
   return(which(is.na(x)))
}
```

## Removing Rows Based on Missing Values in a Column

Sometimes, I do not want to `na.omit()` because it will treat all features equally. I want to check values only for one column.

```
na.rm.feature = function(x, colname)
{
   nas = which(is.na(x[,colname]))
   x = x[-nas, ]
   return(x)
}
```

## Find row where a condition is satisfied

This function can find observations that satisfy a condition. Typically, they are useful in finding specific elements. It is kind of a wrapper around dplyr's `filter()`.

```{r}
which.this = function(df, x)
{
  df %>% 
    filter(eval(parse(text = x)))
}
```

#### Example

```{r}
which.this(iris, "Sepal.Length > 5")
```

## Remove commas, dollars, or any other such characters

```{r}
x = gsub(",", "", x)
```

## GGPlot2 Theme

See [official guide](https://ggplot2.tidyverse.org/reference/theme.html) for more details. Also see [Benjamin's blog](https://benjaminlouis-stat.fr/en/blog/2020-05-21-astuces-ggplot-rmarkdown/).

```{r}
theme_h = function(base_size = 14) {
  theme_bw(base_size = base_size) %+replace%
    theme(
      # Specify plot title
      plot.title = element_text(size = rel(1), face = "bold", margin = margin(0,0,5,0), hjust = 0),
      # Specifying grid and border
      panel.grid.minor = element_blank(),
      panel.border = element_blank(),
      # Specidy axis details
      axis.title = element_text(size = rel(0.85), face = "bold"),
      axis.text = element_text(size = rel(0.70), face = "bold"),
      axis.line = element_line(color = "black", arrow = arrow(length = unit(0.3, "lines"), type = "closed")),
      # Specify legend details
      legend.title = element_text(size = rel(0.85), face = "bold"),
      legend.text = element_text(size = rel(0.70), face = "bold"),
      legend.key = element_rect(fill = "transparent", colour = NA),
      legend.key.size = unit(1.5, "lines"),
      legend.background = element_rect(fill = "transparent", colour = NA),
      # Remove default background
      strip.background = element_rect(fill = "#17252D", color = "#17252D"),
      strip.text = element_text(size = rel(0.85), face = "bold", color = "white", margin = margin(5,0,5,0))
    )
}
```


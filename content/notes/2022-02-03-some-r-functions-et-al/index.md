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

This function opens the data frame in Excel. Original credits to Bruno Rodrigues.

<blockquote class="twitter-tweet"><p lang="en" dir="ltr">Little <a href="https://twitter.com/hashtag/RStats?src=hash&amp;ref_src=twsrc%5Etfw">#RStats</a> function I use when I quickly need to open the result of various %&gt;% operations in Excel<br><br>as in : mtcars %&gt;% filter(am == 1) %&gt;% show_in_excel() <a href="https://t.co/HfJm9jOxVu">pic.twitter.com/HfJm9jOxVu</a></p>&mdash; Bruno Rodrigues (@brodriguesco) <a href="https://twitter.com/brodriguesco/status/1447468259725434886?ref_src=twsrc%5Etfw">October 11, 2021</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

```{r}
show_in_excel = function(.data)
{
   temp = paste0(tempfile(), ".csv")
   write.csv(.data, temp)
   fs::file_show(path = temp)
}
```

This can be used with pipes.

```{r}
iris %>% 
  show_in_excel()
```

## Convert Missing Values to Zero

This function converts missing values in a vector to zero.

```{r}
n2z = function(x)
{
   x = ifelse(is.na(x), 0, x)
   return(x)
}
```

## Finding Index of Missing Elements

This function returns index of elements which are missing. Very useful in finding what observations are missing.

```{r}
which.na = function(x)
{
   return(which(is.na(x)))
}
```

## Removing Rows Based on Missing Values in a Column

Sometimes, I do not want to `na.omit()` because it will treat all features equally. I want to check values only for one column.

```{r}
na.rm.feature = function(x, colname)
{
   # this function removes rows which have missing value in a column
   nas = which(is.na(x[,colname]))
   x = x[-nas, ]
   return(x)
}
```



























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
   # this function removes rows which have missing value in a column
   nas = which(is.na(x[,colname]))
   x = x[-nas, ]
   return(x)
}
```

## Find Row where x==5

```{r}

```

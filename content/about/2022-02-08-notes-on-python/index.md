---
title: Notes on Python
subtitle: Some things that I'll likely forget
summary: Some things that I'll likely forget
author: Harshvardhan
date: '2022-02-08'
slug: notes-on-python
categories:
  - Python
tags: []
---

## Installing Packages

There are ~~two~~ three ways: `pip`, `conda` and within Jupyter Hub. If you are using Anaconda (Navigator), use `conda`. `pip` will install for all environments; `conda` will install for conda environment only. Put either of these codes in Terminal.


```r
# using pip
python -m pip install <package>

# using conda
conda install <package>
```

If it is a one off use case (which it usually never is), use the following command.


```r
!pip install <package>
```

## Methods to Print

There are two methods: `print()` and `pprint()`. They both serve the save cause but `pprint()` is better at displaying complex data structures such as list of lists or JSON files.

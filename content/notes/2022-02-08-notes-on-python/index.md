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

## Terminal in Jupyter

Terminal commands can be passed within the Jupyter notebook, just like the `pip install` command described earlier. Any command starting with `!` would be run like a terminal command within the Jupyter notebook.


```r
# list all files in current directory
!ls

# delete all files in the current folder
!rm -r *
```

## Debugging in the Current State

Many a time our code crashes and we would like to investigate the environment at that moment. Running `%debug` in Jupyter Notebook immediately after the code crashes would open a debugging environment where you can see variables' values, etc.


```python
# some code that crashed
x = some_function(y)

# in the next Jupyter cell, run this command
%debug
```

## Printing

There are two methods: `print()` and `pprint()`. They both serve the save cause but `pprint()` is better at displaying complex data structures such as list of lists or JSON files.

It is worthwhile to mention `f`-strings. They are usually more compact than writing full print statements. Furthermore, if you want to print value of a variable, they're really short.


```python
# enclose the variable in curly braces
print(f"Value of x is {x}")

# if you want to just print the value of, use {x=}
print(f"{x=}")
```

## Adding Rows

It is more efficient to create a list of rows first and then convert it to a pandas data frame. As qmeeus [said](https://stackoverflow.com/questions/55967976/python-panda-append-dataframe-in-loop?noredirect=1&lq=1) on SO,

> Pandas dataframes do not work as a list, they are much more complex data structures and appending is not really considered the best approach.


```r
data = []
for row in some_function_that_yields_data():
    data.append(row)

# either this
df = pd.DataFrame(data)

# or this
df = pd.concat([results, df], axis=0).reset_index(drop=True)
```

## See Details of a Function

To see details of a function in a Jupyter notebook, use `??` operator. It will show you the body and the associated documentation (if available).


```r
??my_function()
```

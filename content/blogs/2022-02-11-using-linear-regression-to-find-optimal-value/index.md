---
title: Linear Regression and Optimisation
subtitle: Using linear regression to find the optimal value of an input
summary: Using linear regression to find the optimal value of an input
author: Harshvardhan
date: '2022-02-11'
slug: using-linear-regression-to-find-optimal-value
categories:
  - R
  - statistics
tags: []
---

When I was first introduced to linear regression for the first time six years ago, I was surprised by its power. I could not only know the effect of one phenomenon on another but I could also know the extent of relationship. As years passed by, I revisited its different parts in pieces. Stability. Consistency. Precision. R Squared. The list goes on.

Sometime in past, I decided to compile all I had learnt about linear regression. However, such huge projects never see fruition. [Prof Amlesh Sharma](https://mays.tamu.edu/directory/as19/) from Texas A&M taught in his Advanced Marketing Analytics class in my MBA; I didn't find this technique elsewhere. Using this simple trick, you can decide the optimal value for an input to produce the maximum output.

# Formulation

At its heart, linear regression is fitting a straight line in the existing data to such that the line is closest to the points. In fact, the optimisation problem we solve for is to minimise the distance between the line and the true value. This approach is called "loss minimisation". Another popular method is to "maximise likelihood". Both these methods are beyond the scope of this article.

# Variables

**Independent variables (X):** Independent variables are assumed to be independent of each other and to be the cause of an effect.

**Dependent variable (Y):** Dependent variable is the final effect we try to estimate or predict.

# Case Study: Number of Golf Courses

There is a strong theoritical reason to believe that the number of golf courses in a state would depend on factors such as climate, population, how rich are people who live there, how popular is golf in that area. Consider a simple case where you know only the population of the state and the number of golf courses in that state.

The linear model to find the number of gold courses can be written as the following.

$$
Y = \beta_0 + \beta_1X \varepsilon
$$

`\(Y\)` is the number of golf courses in the state and `\(X\)` is population.

## Is the relationship linear?

Let's check it.

### Data

Data on golf courses by US state is available at this [website](https://www.bls.gov/opub/ted/2018/golf-anyone-a-look-at-golf-courses-and-country-clubs-by-state.htm). I scrapped it into a `.CSV` file available [here](data/golf.csv).


```r
#df = read.csv("")
```

![](index.md)

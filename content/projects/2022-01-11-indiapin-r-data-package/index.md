---
title: 'IndiaPIN: R Data Package'
subtitle: 'R Package for All India PIN Codes Directory with Latitude and Longitude Details (Updated: December 2021)'
summary: 'R Package for All India PIN Codes Directory with Latitude and Longitude Details (Updated: December 2021)'
author: Harshvardhan
date: '2022-01-11'
slug: IndiaPIN
categories:
  - R
  - package
tags: []
links:
- icon: github
  icon_pack: fab
  name: GitHub Repository
  url: https://github.com/harshvardhaniimi/IndiaPIN
---

`IndiaPIN` contains geographic details about 19,300 PIN codes in India. Some PIN codes had more than one offices. Only the first office of that PIN code area has been retained in those cases. (Updated: December 2021.)

{{% tweet "1477646394479493122" %}}

## Variables

1.  **Circle:** (chr) Name of the Postal Circle
2.  **Region:** (chr) Name of the Postal Region
3.  **Division:** (chr) Name of the Postal Division
4.  **Office:** (chr) Name of Postal Office
5.  **PIN:** (int) Six-digit PIN Code
6.  **District:** (chr) Name of the District
7.  **State:** (chr) Name of the State
8.  **Latitude:** (dbl) Latitude
9.  **Longitude:** (dbl) Longitude

### Data Source

Department of Posts, Ministry of Communications, Government of India. URL: https://www.indiapost.gov.in/vas/pages/findpincode.aspx. Wrangled for this package by Harshvardhan (https://harsh17.in/).

------------------------------------------------------------------------

## Installation

``` r
# install `devtools` if not already installed
if (!require("IndiaPIN")) 
    devtools::install_github("harshvardhaniimi/IndiaPIN")
```

    ## Loading required package: IndiaPIN

``` r
# Tidyverse
library(tidyverse)
```

    ## ── Attaching packages ─────────────────────────────────────── tidyverse 1.3.1 ──

    ## ✓ ggplot2 3.3.5          ✓ purrr   0.3.4     
    ## ✓ tibble  3.1.6          ✓ dplyr   1.0.7.9000
    ## ✓ tidyr   1.1.4          ✓ stringr 1.4.0     
    ## ✓ readr   2.0.2          ✓ forcats 0.5.1

    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## x dplyr::filter() masks stats::filter()
    ## x dplyr::lag()    masks stats::lag()

``` r
# load IndiaPIN
library(IndiaPIN)
data(IndiaPIN)
```

## Example

### Data and Variables

``` r
IndiaPIN
```

    ## # A tibble: 19,300 × 9
    ## # Groups:   PIN [19,300]
    ##    Circle   Region   Division   Office     PIN District State Latitude Longitude
    ##    <chr>    <chr>    <chr>      <chr>    <int> <chr>    <chr>    <dbl>     <dbl>
    ##  1 Andhra … Kurnool… Hindupur … Peddak… 515631 ANANTAP… ANDH…     14.6      77.9
    ##  2 Andhra … Kurnool… Hindupur … Obular… 515581 ANANTAP… ANDH…     14.2      78.3
    ##  3 Andhra … Kurnool… Hindupur … Gurram… 515571 ANANTAP… ANDH…     13.9      78.2
    ##  4 Andhra … Kurnool… Hindupur … Hallik… 515311 ANANTAP… ANDH…     13.8      77.0
    ##  5 Andhra … Kurnool… Hindupur … Tammad… 515281 ANANTAP… ANDH…     14.1      77.0
    ##  6 Andhra … Kurnool… Hindupur … Bussai… 515241 ANANTAP… ANDH…     14.0      77.7
    ##  7 Andhra … Vijayaw… Tadepalli… Kavulu… 534176 WEST GO… ANDH…     16.6      80.6
    ##  8 Bihar C… East Re… Bhagalpur… Kathra… 813105 BANKA    BIHAR     84.5      24.2
    ##  9 Bihar C… East Re… Bhagalpur… Kasri … 813203 BHAGALP… BIHAR     87.3      25.3
    ## 10 Bihar C… East Re… Bhagalpur… Akidat… 853202 BHAGALP… BIHAR     25.4      84.3
    ## # … with 19,290 more rows

### Number of PIN codes by State/UT

``` r
IndiaPIN %>% 
  group_by(State) %>% 
  summarise(Count = n()) %>% 
  arrange(desc(Count)) %>% 
  print(n = 40)
```

    ## # A tibble: 36 × 2
    ##    State                                        Count
    ##    <chr>                                        <int>
    ##  1 TAMIL NADU                                    2036
    ##  2 UTTAR PRADESH                                 1652
    ##  3 MAHARASHTRA                                   1585
    ##  4 KERALA                                        1425
    ##  5 KARNATAKA                                     1347
    ##  6 ANDHRA PRADESH                                1228
    ##  7 WEST BENGAL                                   1128
    ##  8 GUJARAT                                       1007
    ##  9 RAJASTHAN                                     1004
    ## 10 ODISHA                                         935
    ## 11 BIHAR                                          857
    ## 12 MADHYA PRADESH                                 770
    ## 13 TELANGANA                                      674
    ## 14 ASSAM                                          572
    ## 15 PUNJAB                                         534
    ## 16 HIMACHAL PRADESH                               436
    ## 17 JHARKHAND                                      380
    ## 18 HARYANA                                        315
    ## 19 UTTARAKHAND                                    300
    ## 20 CHHATTISGARH                                   274
    ## 21 JAMMU AND KASHMIR                              196
    ## 22 DELHI                                           97
    ## 23 GOA                                             88
    ## 24 TRIPURA                                         80
    ## 25 MEGHALAYA                                       68
    ## 26 MANIPUR                                         52
    ## 27 ARUNACHAL PRADESH                               49
    ## 28 MIZORAM                                         47
    ## 29 NAGALAND                                        43
    ## 30 CHANDIGARH                                      25
    ## 31 ANDAMAN AND NICOBAR ISLANDS                     22
    ## 32 PUDUCHERRY                                      22
    ## 33 SIKKIM                                          19
    ## 34 LADAKH                                          16
    ## 35 LAKSHADWEEP                                      9
    ## 36 THE DADRA AND NAGAR HAVELI AND DAMAN AND DIU     8

More examples will be added in time. See [Github](https://github.com/harshvardhaniimi/IndiaPIN) for source code.
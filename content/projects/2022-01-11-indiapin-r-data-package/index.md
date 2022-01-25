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

<script src="{{< blogdown/postref >}}index_files/htmlwidgets/htmlwidgets.js"></script>
<script src="{{< blogdown/postref >}}index_files/jquery/jquery.min.js"></script>
<link href="{{< blogdown/postref >}}index_files/leaflet/leaflet.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/leaflet/leaflet.js"></script>
<link href="{{< blogdown/postref >}}index_files/leafletfix/leafletfix.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/proj4/proj4.min.js"></script>
<script src="{{< blogdown/postref >}}index_files/Proj4Leaflet/proj4leaflet.js"></script>
<link href="{{< blogdown/postref >}}index_files/rstudio_leaflet/rstudio_leaflet.css" rel="stylesheet" />
<script src="{{< blogdown/postref >}}index_files/leaflet-binding/leaflet.js"></script>

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

    ## # A tibble: 18,169 × 9
    ## # Groups:   PIN [18,169]
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
    ## # … with 18,159 more rows

### Number of PIN codes by State/UT

``` r
IndiaPIN %>% 
  group_by(State) %>% 
  summarise(Count = n()) %>% 
  arrange(desc(Count)) %>% 
  print(n = 40)
```

    ## # A tibble: 35 × 2
    ##    State                                        Count
    ##    <chr>                                        <int>
    ##  1 TAMIL NADU                                    2032
    ##  2 UTTAR PRADESH                                 1581
    ##  3 MAHARASHTRA                                   1466
    ##  4 KERALA                                        1425
    ##  5 KARNATAKA                                     1188
    ##  6 WEST BENGAL                                   1125
    ##  7 ANDHRA PRADESH                                1071
    ##  8 GUJARAT                                       1007
    ##  9 RAJASTHAN                                      986
    ## 10 ODISHA                                         933
    ## 11 BIHAR                                          853
    ## 12 MADHYA PRADESH                                 760
    ## 13 ASSAM                                          571
    ## 14 PUNJAB                                         531
    ## 15 TELANGANA                                      482
    ## 16 HIMACHAL PRADESH                               436
    ## 17 JHARKHAND                                      360
    ## 18 HARYANA                                        310
    ## 19 UTTARAKHAND                                    300
    ## 20 CHHATTISGARH                                   240
    ## 21 JAMMU AND KASHMIR                              195
    ## 22 DELHI                                           97
    ## 23 GOA                                             88
    ## 24 CHANDIGARH                                      25
    ## 25 PUDUCHERRY                                      22
    ## 26 SIKKIM                                          19
    ## 27 MEGHALAYA                                       16
    ## 28 TRIPURA                                         10
    ## 29 MIZORAM                                          9
    ## 30 THE DADRA AND NAGAR HAVELI AND DAMAN AND DIU     8
    ## 31 LAKSHADWEEP                                      7
    ## 32 ARUNACHAL PRADESH                                5
    ## 33 NAGALAND                                         5
    ## 34 ANDAMAN AND NICOBAR ISLANDS                      4
    ## 35 LADAKH                                           2

### PIN Code Locations on Map

I will use `leaflet` package to plot randomly selected 50 PIN codes. I am adding the Region and Circle name in the popup.

``` r
library(leaflet)
library(tidyverse)
library(IndiaPIN)

data("IndiaPIN")

index = sample(nrow(IndiaPIN), 50)
data = IndiaPIN::IndiaPIN[index,]

l1 = data$Longitude
l2 = data$Latitude
pop = paste(data$Region, data$Circle, sep = ", ")

m = leaflet() %>% 
   addTiles() %>% 
   addMarkers(lng=l1, lat=l2, popup = pop)

m
```

<div id="htmlwidget-1" style="width:672px;height:480px;" class="leaflet html-widget"></div>
<script type="application/json" data-for="htmlwidget-1">{"x":{"options":{"crs":{"crsClass":"L.CRS.EPSG3857","code":null,"proj4def":null,"projectedBounds":null,"options":{}}},"calls":[{"method":"addTiles","args":["//{s}.tile.openstreetmap.org/{z}/{x}/{y}.png",null,null,{"minZoom":0,"maxZoom":18,"tileSize":256,"subdomains":"abc","errorTileUrl":"","tms":false,"noWrap":false,"zoomOffset":0,"zoomReverse":false,"opacity":1,"zIndex":1,"detectRetina":false,"attribution":"&copy; <a href=\"http://openstreetmap.org\">OpenStreetMap<\/a> contributors, <a href=\"http://creativecommons.org/licenses/by-sa/2.0/\">CC-BY-SA<\/a>"}]},{"method":"addMarkers","args":[[76.498,23.49,9.35,27.322,26.4445,18.8021216,25.511152,34.104983,22.791345,11.077,11.4918413,11.01,28.38,23.518158,30.904486,25.89,16.5430915,12.896589,24.30578,22.601219,18.5021,15.2965505,30.9666111,29.806955,25.2123131,13.0828056,19.2895,18.1162,10.41,16.2102211,31.45,21.7401498,24.09,29.771657,22.3434,12.975571,30.7016308,20.4633096,25.67816,13.2365463,13.04,11.7225,9.11,11.68,14.684772,13.0469264,28.248607,9.21,22.5388888,24.44],[15.5934,88.63,77.53,80.186,94.151,82.60354,86.476908,74.60939,77.96514,77.51845,78.407171,79.82,77.12,80.140067,77.096736,87.84,77.89463,74.875115,83.046737,72.790291,80.7621,75.7216106,76.3715277,78.609372,85.1231321,80.2789167,78.4385,73.88921,78.86,74.5656595,75.45,71.468053,75.94,79.041905,88.212,77.560338,77.8695896,85.1124248,86.941143,75.7632617,76.11,75.6035,76.5,75.56,79.729477,77.5454255,74.879952,76.78,88.3190555,92.29],null,null,null,{"interactive":true,"draggable":false,"keyboard":true,"title":"","alt":"","zIndexOffset":0,"opacity":1,"riseOnHover":false,"riseOffset":250},["Calicut Region, Kerala Circle","Kolkata Region, West Bengal Circle","Southern Region, Madurai, Tamilnadu Circle","Bareilly Region, Uttar Pradesh Circle","Dibrugarh Region, Assam Circle","Berhampur Region, Odisha Circle","East Region, Bhagalpur, Bihar Circle","DivReportingCircle, Jammukashmir Circle","DivReportingCircle, Madhya Pradesh Circle","Western Region, Coimbatore, Tamilnadu Circle","Western Region, Coimbatore, Tamilnadu Circle","Central Region, Trichirapalli, Tamilnadu Circle","DivReportingCircle, Delhi Circle","Jabalpur Region, Madhya Pradesh Circle","DivReportingCircle, Himachal Pradesh Circle","North Bengal Region, West Bengal Circle","Hyderabad Region, Telangana Circle","South Karnataka Region, Karnataka Circle","Allahabad Region, Uttar Pradesh Circle","Vadodara Region, Gujarat Circle","DivReportingCircle, Chattisgarh Circle","North Karnataka Region, Karnataka Circle","DivReportingCircle, Punjab Circle","DivReportingCircle, Uttarakhand Circle","DivReportingCircle, Bihar Circle","Chennai City Region, Tamilnadu Circle","Bareilly Region, Uttar Pradesh Circle","Pune Region, Maharashtra Circle","Central Region, Trichirapalli, Tamilnadu Circle","North Karnataka Region, Karnataka Circle","Punjab West Region, Punjab Circle","Rajkot Region, Gujarat Circle","Ajmer Region, Rajasthan Circle","DivReportingCircle, Uttarakhand Circle","Kolkata Region, West Bengal Circle","Bengaluru HQ Region, Karnataka Circle","DivReportingCircle, Uttarakhand Circle","DivReportingCircle, Odisha Circle","East Region, Bhagalpur, Bihar Circle","South Karnataka Region, Karnataka Circle","South Karnataka Region, Karnataka Circle","Kochi Region, Kerala Circle","DivReportingCircle, Kerala Circle","Calicut Region, Kerala Circle","Vijayawada Region, Andhra Pradesh Circle","Bengaluru HQ Region, Karnataka Circle","Jodhpur Region, Rajasthan Circle","DivReportingCircle, Kerala Circle","Kolkata Region, West Bengal Circle","DivReportingCircle, Assam Circle"],null,null,null,null,{"interactive":false,"permanent":false,"direction":"auto","opacity":1,"offset":[0,0],"textsize":"10px","textOnly":false,"className":"","sticky":true},null]}],"limits":{"lat":[9.11,76.498],"lng":[15.5934,94.151]}},"evals":[],"jsHooks":[]}</script>

Also see this [Stackoverflow thread](https://stackoverflow.com/questions/31336898/how-to-save-leaflet-in-r-map-as-png-or-jpg-file) to understand how to save the plots.

See [Github](https://github.com/harshvardhaniimi/IndiaPIN) for source code.

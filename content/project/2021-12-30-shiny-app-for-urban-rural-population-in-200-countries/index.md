---
title: Urban-Rural Population in 200+ Countries
subtitle: R Shiny app that creates spreadsheet of population levels segregated at district, state, or any other level
summary: R Shiny app that creates spreadsheet of population levels segregated at district, state, or any other level
author: Harshvardhan
date: '2021-12-30'
slug: shiny-urca
categories: []
tags: []
---

> [Intro slides](https://github.com/harshvardhaniimi/raster-population/blob/main/Slides.pdf) by [Harshvardhan](https://www.harsh17.in)

**The [Github repository](https://github.com/harshvardhaniimi/raster-population) contains codebase and related datasets/databases for Population Raster App.**

The aim is to have a shiny app that creates spreadsheet with state or district level aggregated population for more than 200 country.

- Original raster to be aggregated is regional/country-level population, sourced from Worldpop (https://www.worldpop.org/geodata/listing?id=75).
- Partitioning raster could be: Urban-rural classification, Time-to-healthcare unit, etc.
- Level of partitioning will be decided by the user in runtime.

**The current app supports Urban-Rural classification for more than 200 countries and regions.**

### Limitations of Current Version

- The app is as slow as snail,
- It only supports urban-rural classification for partitioning,
- It only works for year 2020.

## Future Work

### High Priority 

- Redesign the app with partitioning raster instead of country as focus. Instead of having the choices at the navigation bar, the users should see a single screen
where they choose the country and the partitioning raster (possibly multiple partioning rasters).

- Improving runtime speed (AWS web hosting and better caching can be explored). Currently, the app downloads population and mappings of the country for the 
first time and reuses them when required. 

For example, when you search the population for Latvia for the first time, it will download the relevant files and save 
them for future use. Next time someone uses the app again for Latvia, the processing will be faster as the files are already available offline.

### Low Priority

- Include support for years other than 2020. This is not a difficult thing to pull off but would require extensive computing resource, beyond what a laptop can provide.

## P.S.

I do not work or engage with ASAR anymore. Due to other commitments, I had to drop this project. This app, despite its limitations, is useful.

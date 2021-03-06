---
title       : My shiny app
subtitle    : Illustration of similarities of wind speed observation stations over Europe
author      : SL
job         : PhD student at some research institute in Germany
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

## Motivation for my app: Basics

Together with a coworker, I am working on wind speed prediction models. We have a new data set with observations and forecasts for observation stations in Europe.

Our idea is to "borrow" informations from similar stations in the model estimation process. To that end, we want to investigate different ways to find "similar" stations.

My aim with this app is to develop a visual tool to investigate which stations are similar to each other if the different distance functions are applied.

In particular, the user can choose

1. A distance functions (drop-down selection of 4 possible functions)
2. A station ID (numerical input between 1 and 1739)
3. A number of close stations to be displayed


---

## Details on the plot

The plot then shows:

1. The chosen station in blue
2. The close stations in red
3. All other stations in gray

Also, additional information is displayed:

1. The location identifier of the chosen station (missing for some stations)
2. A short description of the chosen distance function

---

## Behind the scenes

All relevant data are saved in an .Rdata file, and the app extracts the required data from this Rdata file.

As a simple example, assume that I have some variables


```r
stationID <- 1:10
i <- 3
stations.by.distance <- list()
for(i in 1:10){stations.by.distance[[i]] <- sample(stationID[-c(i)], 9)}
```

Then I can get the IDs of the L stations that are the closest to station i by


```r
L <- 5
stations.by.distance[[i]][1:L]
```

```
## [1] 4 1 6 3 5
```

---

## Future work

There are some things I would maybe like to do in the future:

1. Plot the points on an actual map of Europe. So far, this was difficult as we only have to coordinates on the model grid and are still working on matching those to actual geographical coordinates in the real world.
2. Include more distance functions.
3. Add another level of interactivity by allowing the user to choose a station by clicking on the corresponding point in the plot.



Developing Data Products Computer Hardware Relative CPU Performance
========================================================
author: Ray Han
date: 10/27/2015



Background
========================================================
The Data comes from the UC Irvine Machine Learning Repository Web Page. For the Shiny app the user enters information about the computer and then the user gets a predicted CPU Performance Measure. UC Irvine has a leading CS department and there repository is large and comprehensive.

Methodology
========================================================
Here is the part of code which implements the algorithm

```r
library(caret)
library(shiny)
library(UsingR)
#code outside gets run only once outside of function
CompHardware <- read.csv("w:/Ray/CompHardware.csv")
FittedModel <- glm(ERP~MYCT + MMIN + MMAX + CACH + CHMIN + CHMAX + PRP, data=CompHardware)
```
This is a generalized linear model. Other methods are available, but this was the simplest.
The data set is multivariate and the associated tasks are regressions.  So GLM is pretty good 
Algorithm to use.

Shiny Application
========================================================

```r
library(png)
library(grid)
img <- readPNG("W:/Ray/figure1.png")
grid.raster(img)
```

![plot of chunk unnamed-chunk-2](Rpres-figure/unnamed-chunk-2-1.png) 

Check
========================================================
A Plot to show that our algorithm the GLM is good
Fit /published relative performance vs estimated relative performance

```r
expect <- predict(FittedModel, data=CompHardware)
plot(CompHardware$ERP - expect)
```

![plot of chunk unnamed-chunk-3](Rpres-figure/unnamed-chunk-3-1.png) 


---
title       : shiny application
subtitle    : property hunter
author      : Gojibiu
job         : to calculate the rental yield of a property
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

## Instructions

This application is for property investors to calculate the rental yield of a property and estimate the cashflow of owning the property. Your real estate agent and mortgage broker will be able to help you with the numbers.

### Rental Yield
Enter the property's price and expected weekly rental income to calculate the rental yield.
### Cashflow
Enter the property's holding costs to estimate the cashflow of owning the property.

--- .

## Introduction to ui.R
If you want to know the rental yield, you must input some related price.

```r
    textInput('text', 'Address', value='')
    numericInput('price', 'Price ($)', 550000)
    numericInput('weeklyRent', 'Weekly Rent ($)', 550)
    numericInput('weeklyRepayments', 'Weekly Repayments ($ per week)', 503)
    numericInput('strataPerQuarter', 'Strata ($ per quarter)', 1050)
    numericInput('councilPerQuarter', 'Council ($ per quarter)', 163)
    numericInput('waterPerQuarter', 'Water ($ per quarter)', 180)
    numericInput('managementFees', 'Management Fees ($ per week)', 38)
```

--- .

## Introduction to sever.R
There are three functions to calculate the data getting from above.

```r
calculateRentalYield <- function (weeklyRent, propertyPrice) {
  result <- weeklyRent * 52 / propertyPrice * 100
  return(round(result, digits = 2))
}

calculateYearlyCashflow <- function(weeklyRent, strata, council, water, managementFees, weeklyRepayments){
  result <- weeklyRent * 52 - (strata + council + water) * 4 - managementFees * 52 - weeklyRepayments * 52
  return(round(result, digits = 2))
}

calculateWeeklyCashflow <- function(weeklyRent, strata, council, water, managementFees, weeklyRepayments){
  result <- (weeklyRent * 52 - (strata + council + water) * 4 - managementFees * 52 - weeklyRepayments * 52) / 52
  return(round(result, digits = 2))
}
```

--- .

## How to get this app
1. Clone the code using 'git clone https://github.com/Gojibiu/Developing-Data-Products-Assignment.git YOURDIRECTORY'

2. Load your RStudio

3. Set your working directory to YOURDIRECTORY using setwd("YOURDIRECTORY")

4. Load the Shiny library using library(shiny)

5. Run the application using runApp()

6. You will see the application in a browser. Follow the instructions to use the application.

--- .

## Thanks




Thanks for watching my presentation, and wish you happiness!

                                               by Gojibiu



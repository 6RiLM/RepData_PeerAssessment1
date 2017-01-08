# Reproducible Research: Peer Assessment 1
6RiLM  
8 janvier 2017  



Below is the outcome of my work about the week no 2 of the course **Reproductible Research** on [Coursera](https://www.coursera.org/learn/reproducible-research).
I hope this report will be readable enought. In any case, please tell me everything that sounds wrong to you in order to optimize my working method. Thankx

## Loading and preprocessing the data

Before load this dataset let's first unzip the file in the archive. Data file were given on GitHub repository so we do not have to directly download it.


```r
data.path <- "../../Data/Raw data/"
data.zipFile <- paste(data.path, "activity.zip", sep = "")
unzip(data.zipFile, exdir = data.path)
```

Then let's have a look to this new dataset:  


```r
require(dplyr)
require(data.table)
require(lubridate)
data <- tbl_df(fread(paste(data.path, "activity.csv", sep = ""))) %>%
    mutate(date = ymd(date))
head(data, 3)
```

```
## # A tibble: 3 × 3
##   steps       date interval
##   <int>     <date>    <int>
## 1    NA 2012-10-01        0
## 2    NA 2012-10-01        5
## 3    NA 2012-10-01       10
```

```r
data.size <- dim(data)
```

This dataset contains **17568 records** described by **3 features**.


## What is mean total number of steps taken per day?



## What is the average daily activity pattern?



## Imputing missing values


```r
colSums(sapply(data, is.na))
```

```
##    steps     date interval 
##     2304        0        0
```

```r
str(data)
```

```
## Classes 'tbl_df', 'tbl' and 'data.frame':	17568 obs. of  3 variables:
##  $ steps   : int  NA NA NA NA NA NA NA NA NA NA ...
##  $ date    : Date, format: "2012-10-01" "2012-10-01" ...
##  $ interval: int  0 5 10 15 20 25 30 35 40 45 ...
```


## Are there differences in activity patterns between weekdays and weekends?

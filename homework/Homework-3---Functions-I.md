-   [Homework 3 - Functions I](#homework-3---functions-i)
    -   [Write a function that takes a single numerical vector and
        returns three values, the minimum number, the median, and the
        maximum number of the vector. Test your function using the month
        column of the flights
        dataset.](#write-a-function-that-takes-a-single-numerical-vector-and-returns-three-values-the-minimum-number-the-median-and-the-maximum-number-of-the-vector.-test-your-function-using-the-month-column-of-the-flights-dataset.)
        -   [loading dataset](#loading-dataset)
        -   [construct min_med_max
            function](#construct-min_med_max-function)
    -   [Explain your reasoning for choosing your function’s name in the
        previous
        question.](#explain-your-reasoning-for-choosing-your-functions-name-in-the-previous-question.)
    -   [Write a function that categorizes a numerical variable in the
        flights data into four
        categories.](#write-a-function-that-categorizes-a-numerical-variable-in-the-flights-data-into-four-categories.)
    -   [Explain your reasoning for choosing your function’s name in the
        previous
        question.](#explain-your-reasoning-for-choosing-your-functions-name-in-the-previous-question.-1)
    -   [Write a function that calculates the median of all numeric
        variables in the flights dataset using a s`for`
        loop.](#write-a-function-that-calculates-the-median-of-all-numeric-variables-in-the-flights-dataset-using-a-sfor-loop.)
    -   [Explain your reasoning for choosing your function’s name in the
        previous
        question.](#explain-your-reasoning-for-choosing-your-functions-name-in-the-previous-question.-2)

# Homework 3 - Functions I

## Write a function that takes a single numerical vector and returns three values, the minimum number, the median, and the maximum number of the vector. Test your function using the month column of the flights dataset.

### loading dataset

``` r
library(nycflights13)
```

    ## Warning: 程辑包'nycflights13'是用R版本4.1.3 来建造的

``` r
library(tidyverse)
```

    ## -- Attaching packages --------------------------------------- tidyverse 1.3.1 --

    ## v ggplot2 3.3.5     v purrr   0.3.4
    ## v tibble  3.1.2     v dplyr   1.0.7
    ## v tidyr   1.1.3     v stringr 1.4.0
    ## v readr   1.4.0     v forcats 0.5.1

    ## -- Conflicts ------------------------------------------ tidyverse_conflicts() --
    ## x dplyr::filter() masks stats::filter()
    ## x dplyr::lag()    masks stats::lag()

### construct min_med_max function

``` r
min_med_max <- function(x) {
  c(min(x), median(x), max(x))
}

min_med_max(flights$month)
```

    ## [1]  1  7 12

## Explain your reasoning for choosing your function’s name in the previous question.

I chose the name min_med_max because it is descriptive of what the
function does. It takes a vector and returns the minimum, median, and
maximum values of the vector.

## Write a function that categorizes a numerical variable in the flights data into four categories.

``` r
categorize_time <- function(data, column) {
  data %>% select(column) %>%
    mutate(time = case_when(
      column >= 500 & column <= 1159 ~ "Morning",
      column >= 1200 & column <= 1659 ~ "Afternoon",
      column >= 1700 & column <= 2059 ~ "Evening",
      column >= 2100 | column <= 459 ~ "Night"
    ))
}

result<-categorize_time(flights, 'dep_time')
```

    ## Note: Using an external vector in selections is ambiguous.
    ## i Use `all_of(column)` instead of `column` to silence this message.
    ## i See <https://tidyselect.r-lib.org/reference/faq-external-vector.html>.
    ## This message is displayed once per session.

``` r
head(result,10)
```

    ## # A tibble: 10 x 2
    ##    dep_time time 
    ##       <int> <chr>
    ##  1      517 Night
    ##  2      533 Night
    ##  3      542 Night
    ##  4      544 Night
    ##  5      554 Night
    ##  6      554 Night
    ##  7      555 Night
    ##  8      557 Night
    ##  9      557 Night
    ## 10      558 Night

## Explain your reasoning for choosing your function’s name in the previous question.

I chose the name categorize_time because it is descriptive of what the
function does. It takes a data object and a column name and returns a
new column with the values categorized into four categories.

## Write a function that calculates the median of all numeric variables in the flights dataset using a s`for` loop.

``` r
flights_numeric_vars<-select_if(flights, is.numeric)
result.median <- 0

median_for <- function(data) {
  for (i in names(data)) {
    print(median(data[[i]], na.rm = TRUE))
  } 
}
median_for.result <- median_for(flights_numeric_vars)
```

    ## [1] 2013
    ## [1] 7
    ## [1] 16
    ## [1] 1401
    ## [1] 1359
    ## [1] -2
    ## [1] 1535
    ## [1] 1556
    ## [1] -5
    ## [1] 1496
    ## [1] 129
    ## [1] 872
    ## [1] 13
    ## [1] 29

## Explain your reasoning for choosing your function’s name in the previous question.

I chose the name median_for because it is descriptive of what the
function does. It takes a data object and returns the median of all
numeric variables in the data object by using a for loop.

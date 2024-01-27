wk2-workshop
================
TW
2024-01-27

- [Qn1. Find the following statistics about the S&P
  returns.](#qn1-find-the-following-statistics-about-the-sp-returns)
- [Qn2. Create a plot that shows the prices of S&P in this
  period.](#qn2-create-a-plot-that-shows-the-prices-of-sp-in-this-period)
- [Qn3. Create a plot that shows the total yearly returns of S&P from
  2001 to
  2023.](#qn3-create-a-plot-that-shows-the-total-yearly-returns-of-sp-from-2001-to-2023)

``` r
library(tidyverse)
library(lubridate)
```

``` r
df = readRDS("data/wk2_stocks.rds")
str(df)
```

    ## 'data.frame':    5798 obs. of  4 variables:
    ##  $ SPY_prices : num  88.1 87.1 84.3 84.9 84.7 ...
    ##  $ SPY_returns: num  0.04804 -0.01076 -0.03264 0.00774 -0.00264 ...
    ##  $ SPY_vol    : num  88.1 87.1 84.3 84.9 84.7 ...
    ##  $ date       : Date, format: "2001-01-03" "2001-01-04" ...

## Qn1. Find the following statistics about the S&P returns.

The cumulative returns of the S&P index during this period is 218.33%.
The average daily returns of the S&P index during this period is 0.04%.
The standard deviation of the daily returns of the S&P index during this
period is 1.22%.

## Qn2. Create a plot that shows the prices of S&P in this period.

``` r
ggplot(data = df, aes(x = date, y = SPY_prices)) +
  geom_line()
```

![](wk2-workshop_files/figure-gfm/unnamed-chunk-3-1.png)<!-- -->

## Qn3. Create a plot that shows the total yearly returns of S&P from 2001 to 2023.

``` r
df1 = df %>%
  mutate(year = year(date)) %>% 
  group_by(year) %>% 
  filter(year %in% (2001:2023)) %>% 
  summarise(yearly_return = sum(SPY_returns)*100)

ggplot(df1, aes(x = year, y = yearly_return)) +
  geom_col()
```

![](wk2-workshop_files/figure-gfm/unnamed-chunk-4-1.png)<!-- -->

Homework 1
================
Samiha Reza
2024-09-15

# Problem 1

Here is the code chunk for ***data description***.

``` r
data("penguins", package = "palmerpenguins")

summary(penguins)
```

    ##       species          island    bill_length_mm  bill_depth_mm  
    ##  Adelie   :152   Biscoe   :168   Min.   :32.10   Min.   :13.10  
    ##  Chinstrap: 68   Dream    :124   1st Qu.:39.23   1st Qu.:15.60  
    ##  Gentoo   :124   Torgersen: 52   Median :44.45   Median :17.30  
    ##                                  Mean   :43.92   Mean   :17.15  
    ##                                  3rd Qu.:48.50   3rd Qu.:18.70  
    ##                                  Max.   :59.60   Max.   :21.50  
    ##                                  NA's   :2       NA's   :2      
    ##  flipper_length_mm  body_mass_g       sex           year     
    ##  Min.   :172.0     Min.   :2700   female:165   Min.   :2007  
    ##  1st Qu.:190.0     1st Qu.:3550   male  :168   1st Qu.:2007  
    ##  Median :197.0     Median :4050   NA's  : 11   Median :2008  
    ##  Mean   :200.9     Mean   :4202                Mean   :2008  
    ##  3rd Qu.:213.0     3rd Qu.:4750                3rd Qu.:2009  
    ##  Max.   :231.0     Max.   :6300                Max.   :2009  
    ##  NA's   :2         NA's   :2

``` r
nrow(penguins)
```

    ## [1] 344

``` r
ncol(penguins)
```

    ## [1] 8

The “penguins” data includes 8 variables: species, island, bill length
(mm), bill depth (mm), flipper length (mm), body mass (g), sex, and
year. There are three species: Adelie (152 penguins), Chinstrap (68
penguins), and Gentoo (124 penguins). There are three islands: Biscoe
(168 pengiuins), Dream (124 penguins), and Torgersen (52 penguins).
There are 8 columns, and 344 rows, so 344 data samples.The mean flipper
length in mm is 200.9.

Here is the code chunk for the ***scatterplot***

``` r
library(tidyverse)
```

    ## ── Attaching core tidyverse packages ──────────────────────── tidyverse 2.0.0 ──
    ## ✔ dplyr     1.1.4     ✔ readr     2.1.5
    ## ✔ forcats   1.0.0     ✔ stringr   1.5.1
    ## ✔ ggplot2   3.5.1     ✔ tibble    3.2.1
    ## ✔ lubridate 1.9.3     ✔ tidyr     1.3.1
    ## ✔ purrr     1.0.2     
    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()
    ## ℹ Use the conflicted package (<http://conflicted.r-lib.org/>) to force all conflicts to become errors

``` r
ggplot(penguins, aes(x = bill_length_mm, y = flipper_length_mm, color = species)) + geom_point()
```

    ## Warning: Removed 2 rows containing missing values or values outside the scale range
    ## (`geom_point()`).

![](p8105_HW1_sr4081_markdown_files/figure-gfm/scatterplot-1.png)<!-- -->

``` r
ggsave("penguins_scatter.pdf")
```

    ## Saving 7 x 5 in image

    ## Warning: Removed 2 rows containing missing values or values outside the scale range
    ## (`geom_point()`).

# Problem 2

Since we have already loaded tidyverse, we do not need to do it again.
Here we have a code chunk to create the ***data frame***.

``` r
question_2_df = tibble(
  random_sample = rnorm(10),
  logic_vector = random_sample > 0,
  character_vector = rep("character", 10),
  factor_vector = factor(rep(c("Level1", "Level2", "Level3"), length.out =10)),
)

print(question_2_df)
```

    ## # A tibble: 10 × 4
    ##    random_sample logic_vector character_vector factor_vector
    ##            <dbl> <lgl>        <chr>            <fct>        
    ##  1        1.34   TRUE         character        Level1       
    ##  2       -0.700  FALSE        character        Level2       
    ##  3       -1.45   FALSE        character        Level3       
    ##  4       -1.27   FALSE        character        Level1       
    ##  5        0.285  TRUE         character        Level2       
    ##  6       -0.0981 FALSE        character        Level3       
    ##  7       -0.743  FALSE        character        Level1       
    ##  8       -0.0996 FALSE        character        Level2       
    ##  9       -0.213  FALSE        character        Level3       
    ## 10        1.37   TRUE         character        Level1

Here we pull variables from the dataframe and try to find the means of
each.

``` r
random_sample <- question_2_df$random_sample
logic_vector <- question_2_df$logic_vector
character_vector <- question_2_df$character_vector
factor_vector <- question_2_df$factor_vector

mean(random_sample)
```

    ## [1] -0.1579503

``` r
mean(logic_vector)
```

    ## [1] 0.3

``` r
mean(character_vector)
```

    ## Warning in mean.default(character_vector): argument is not numeric or logical:
    ## returning NA

    ## [1] NA

``` r
mean(factor_vector)
```

    ## Warning in mean.default(factor_vector): argument is not numeric or logical:
    ## returning NA

    ## [1] NA

Only random_sample and logic_vector has a mean value. Character and
Factor vector do not because “argument is not numeric or logical.”

We now check if we can convert the variables to numeric ones.

``` r
numeric_logical = as.numeric(logic_vector)
# numeric_character = as.numeric(character_vector)
# numeric_factor = as.numeric(factor)
```

Character and factor vector cannot be converted to numeric, which is why
it isn’t possible to find the mean.

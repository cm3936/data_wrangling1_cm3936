Data Import
================
Carolyn Martinez
2024-09-17

1.  Loading pakcages needed

This document will show hoe to import data from R, not form the files.

*How to tell computer where the file is:*

1.  Absolute path - leads the computer to the root directory

    Some issues - not efficient

2.  Relative path - tells you how to get there from where you are right
    not

*Best practice* Do this by creating an Rproject that contains all the
moving parts of the project.

## Importing the data from the files AND clean the column names

``` r
litters_df = read_csv("data_import_examples/FAS_litters.csv")
```

    ## Rows: 49 Columns: 8
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr (4): Group, Litter Number, GD0 weight, GD18 weight
    ## dbl (4): GD of Birth, Pups born alive, Pups dead @ birth, Pups survive
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
litters_df = janitor::clean_names(litters_df)
```

Note: janitor:: clean_names means “using the function clean_names” in
the janitor package

## Look at the data set

``` r
litters_df
```

    ## # A tibble: 49 × 8
    ##    group litter_number   gd0_weight gd18_weight gd_of_birth pups_born_alive
    ##    <chr> <chr>           <chr>      <chr>             <dbl>           <dbl>
    ##  1 Con7  #85             19.7       34.7                 20               3
    ##  2 Con7  #1/2/95/2       27         42                   19               8
    ##  3 Con7  #5/5/3/83/3-3   26         41.4                 19               6
    ##  4 Con7  #5/4/2/95/2     28.5       44.1                 19               5
    ##  5 Con7  #4/2/95/3-3     <NA>       <NA>                 20               6
    ##  6 Con7  #2/2/95/3-2     <NA>       <NA>                 20               6
    ##  7 Con7  #1/5/3/83/3-3/2 <NA>       <NA>                 20               9
    ##  8 Con8  #3/83/3-3       <NA>       <NA>                 20               9
    ##  9 Con8  #2/95/3         <NA>       <NA>                 20               8
    ## 10 Con8  #3/5/2/2/95     28.5       <NA>                 20               8
    ## # ℹ 39 more rows
    ## # ℹ 2 more variables: pups_dead_birth <dbl>, pups_survive <dbl>

``` r
head(litters_df)
```

    ## # A tibble: 6 × 8
    ##   group litter_number gd0_weight gd18_weight gd_of_birth pups_born_alive
    ##   <chr> <chr>         <chr>      <chr>             <dbl>           <dbl>
    ## 1 Con7  #85           19.7       34.7                 20               3
    ## 2 Con7  #1/2/95/2     27         42                   19               8
    ## 3 Con7  #5/5/3/83/3-3 26         41.4                 19               6
    ## 4 Con7  #5/4/2/95/2   28.5       44.1                 19               5
    ## 5 Con7  #4/2/95/3-3   <NA>       <NA>                 20               6
    ## 6 Con7  #2/2/95/3-2   <NA>       <NA>                 20               6
    ## # ℹ 2 more variables: pups_dead_birth <dbl>, pups_survive <dbl>

``` r
tail(litters_df, 10)
```

    ## # A tibble: 10 × 8
    ##    group litter_number gd0_weight gd18_weight gd_of_birth pups_born_alive
    ##    <chr> <chr>         <chr>      <chr>             <dbl>           <dbl>
    ##  1 Mod8  #7/110/3-2    27.5       46                   19               8
    ##  2 Mod8  #2/95/2       28.5       44.5                 20               9
    ##  3 Mod8  #82/4         33.4       52.7                 20               8
    ##  4 Low8  #53           21.8       37.2                 20               8
    ##  5 Low8  #79           25.4       43.8                 19               8
    ##  6 Low8  #100          20         39.2                 20               8
    ##  7 Low8  #4/84         21.8       35.2                 20               4
    ##  8 Low8  #108          25.6       47.5                 20               8
    ##  9 Low8  #99           23.5       39                   20               6
    ## 10 Low8  #110          25.5       42.7                 20               7
    ## # ℹ 2 more variables: pups_dead_birth <dbl>, pups_survive <dbl>

\##looking at the ENTIRE data frame - opens a new window

``` r
view(litters_df)
```

## Learning Assessment: loading FAS_pups.csv and cleaning the names

``` r
pups_df=read_csv("data_import_examples/FAS_pups.csv")
```

    ## Rows: 313 Columns: 6
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr (2): Litter Number, PD ears
    ## dbl (4): Sex, PD eyes, PD pivot, PD walk
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
pups_df = janitor::clean_names(pups_df)

pups_df
```

    ## # A tibble: 313 × 6
    ##    litter_number   sex pd_ears pd_eyes pd_pivot pd_walk
    ##    <chr>         <dbl> <chr>     <dbl>    <dbl>   <dbl>
    ##  1 #85               1 4            13        7      11
    ##  2 #85               1 4            13        7      12
    ##  3 #1/2/95/2         1 5            13        7       9
    ##  4 #1/2/95/2         1 5            13        8      10
    ##  5 #5/5/3/83/3-3     1 5            13        8      10
    ##  6 #5/5/3/83/3-3     1 5            14        6       9
    ##  7 #5/4/2/95/2       1 .            14        5       9
    ##  8 #4/2/95/3-3       1 4            13        6       8
    ##  9 #4/2/95/3-3       1 4            13        7       9
    ## 10 #2/2/95/3-2       1 4            NA        8      10
    ## # ℹ 303 more rows

## How to make data import seamless

using the ?read_csv command to see the different optns

*looking at the options*

``` r
litters_df=
  read_csv(
    file="data_import_examples/FAS_litters.csv",
    col_names = FALSE,
    skip=1
    )
```

    ## Rows: 49 Columns: 8
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr (4): X1, X2, X3, X4
    ## dbl (4): X5, X6, X7, X8
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

Notes: - skip = 1 allows you to skip lines depending on how the data is
structured. - col_names = false is saying the column names are not
actually the names.

*when you are missing data*

``` r
  litters_df=
  read_csv(
  file="data_import_examples/FAS_litters.csv",
  na=c("NA", "", ".")
)
```

    ## Rows: 49 Columns: 8
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr (2): Group, Litter Number
    ## dbl (6): GD0 weight, GD18 weight, GD of Birth, Pups born alive, Pups dead @ ...
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

*What if we code ‘group’ as a factor variable? - changing variable
types*

``` r
litters_df=
  read_csv(
  file="data_import_examples/FAS_litters.csv",
  na=c("NA", "", "."),
  col_types = cols(
    Group=col_factor()
    )
  )
```

## Importing an Excel File

``` r
mlb_df=read_excel("data_import_examples/mlb11.xlsx", sheet="mlb11")

mlb_df
```

    ## # A tibble: 30 × 12
    ##    team        runs at_bats  hits homeruns bat_avg strikeouts stolen_bases  wins
    ##    <chr>      <dbl>   <dbl> <dbl>    <dbl>   <dbl>      <dbl>        <dbl> <dbl>
    ##  1 Texas Ran…   855    5659  1599      210   0.283        930          143    96
    ##  2 Boston Re…   875    5710  1600      203   0.28        1108          102    90
    ##  3 Detroit T…   787    5563  1540      169   0.277       1143           49    95
    ##  4 Kansas Ci…   730    5672  1560      129   0.275       1006          153    71
    ##  5 St. Louis…   762    5532  1513      162   0.273        978           57    90
    ##  6 New York …   718    5600  1477      108   0.264       1085          130    77
    ##  7 New York …   867    5518  1452      222   0.263       1138          147    97
    ##  8 Milwaukee…   721    5447  1422      185   0.261       1083           94    96
    ##  9 Colorado …   735    5544  1429      163   0.258       1201          118    73
    ## 10 Houston A…   615    5598  1442       95   0.258       1164          118    56
    ## # ℹ 20 more rows
    ## # ℹ 3 more variables: new_onbase <dbl>, new_slug <dbl>, new_obs <dbl>

``` r
pulse_df=read_sas("data_import_examples/public_pulse_data.sas7bdat")

pulse_df
```

    ## # A tibble: 1,087 × 7
    ##       ID   age Sex    BDIScore_BL BDIScore_01m BDIScore_06m BDIScore_12m
    ##    <dbl> <dbl> <chr>        <dbl>        <dbl>        <dbl>        <dbl>
    ##  1 10003  48.0 male             7            1            2            0
    ##  2 10015  72.5 male             6           NA           NA           NA
    ##  3 10022  58.5 male            14            3            8           NA
    ##  4 10026  72.7 male            20            6           18           16
    ##  5 10035  60.4 male             4            0            1            2
    ##  6 10050  84.7 male             2           10           12            8
    ##  7 10078  31.3 male             4            0           NA           NA
    ##  8 10088  56.9 male             5           NA            0            2
    ##  9 10091  76.0 male             0            3            4            0
    ## 10 10092  74.2 female          10            2           11            6
    ## # ℹ 1,077 more rows

## Never use read.csv()

This is not good because it does not give a lot of info on the data -
missing the type of variables and how the data is coded

## Never do this - you should not be removing the variables from the data -\> EVER

``` r
litters_df$L
```

    ## Warning: Unknown or uninitialised column: `L`.

    ## NULL

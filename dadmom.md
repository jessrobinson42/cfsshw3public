Tidying `dadmom`
================
Jess Robinson

Get the data
============

``` r
# don't modify this chunk unless you still need to install rcfss
# if so, run "devtools::install_github("uc-cfss/rcfss")" in the console first

library(tidyverse)
```

    ## ── Attaching packages ──────────────────────────────────────────────────── tidyverse 1.2.1 ──

    ## ✔ ggplot2 3.0.0     ✔ purrr   0.2.5
    ## ✔ tibble  1.4.2     ✔ dplyr   0.7.6
    ## ✔ tidyr   0.8.1     ✔ stringr 1.3.1
    ## ✔ readr   1.1.1     ✔ forcats 0.3.0

    ## Warning: package 'dplyr' was built under R version 3.5.1

    ## ── Conflicts ─────────────────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()

``` r
library(rcfss)
library(knitr)
data("dadmom")
dadmom
```

    ## # A tibble: 3 x 5
    ##   famid named  incd namem  incm
    ##   <dbl> <chr> <dbl> <chr> <dbl>
    ## 1     1 Bill  30000 Bess  15000
    ## 2     2 Art   22000 Amy   18000
    ## 3     3 Paul  25000 Pat   50000

Tidied data
===========

``` r
#tidying data
kable(dadmom %>% 
  gather(key = key, value= value, "named", "namem", "incd", "incm") %>% 
  separate(col= key, into=c("variable", "Parent Type"), sep = -1)  %>% 
  spread(key=variable, value = value) %>% 
  rename("Income" = inc, "First Name" = name, "Family ID" = famid))
```

|  Family ID| Parent Type | Income | First Name |
|----------:|:------------|:-------|:-----------|
|          1| d           | 30000  | Bill       |
|          1| m           | 15000  | Bess       |
|          2| d           | 22000  | Art        |
|          2| m           | 18000  | Amy        |
|          3| d           | 25000  | Paul       |
|          3| m           | 50000  | Pat        |

Session info
------------

``` r
# don't modify this chunk
devtools::session_info()
```

    ## ─ Session info ──────────────────────────────────────────────────────────
    ##  setting  value                       
    ##  version  R version 3.5.0 (2018-04-23)
    ##  os       OS X El Capitan 10.11.6     
    ##  system   x86_64, darwin15.6.0        
    ##  ui       X11                         
    ##  language (EN)                        
    ##  collate  en_US.UTF-8                 
    ##  ctype    en_US.UTF-8                 
    ##  tz       America/Chicago             
    ##  date     2019-04-22                  
    ## 
    ## ─ Packages ──────────────────────────────────────────────────────────────
    ##  package     * version date       lib source                        
    ##  assertthat    0.2.0   2017-04-11 [1] CRAN (R 3.5.0)                
    ##  backports     1.1.2   2017-12-13 [1] CRAN (R 3.5.0)                
    ##  base64enc     0.1-3   2015-07-28 [1] CRAN (R 3.5.0)                
    ##  bindr         0.1.1   2018-03-13 [1] CRAN (R 3.5.0)                
    ##  bindrcpp      0.2.2   2018-03-29 [1] CRAN (R 3.5.0)                
    ##  broom         0.5.0   2018-07-17 [1] CRAN (R 3.5.0)                
    ##  callr         3.0.0   2018-08-24 [1] CRAN (R 3.5.0)                
    ##  cellranger    1.1.0   2016-07-27 [1] CRAN (R 3.5.0)                
    ##  cli           1.0.0   2017-11-05 [1] CRAN (R 3.5.0)                
    ##  colorspace    1.3-2   2016-12-14 [1] CRAN (R 3.5.0)                
    ##  crayon        1.3.4   2017-09-16 [1] CRAN (R 3.5.0)                
    ##  desc          1.2.0   2018-05-01 [1] CRAN (R 3.5.0)                
    ##  devtools      2.0.1   2018-10-26 [1] CRAN (R 3.5.0)                
    ##  digest        0.6.15  2018-01-28 [1] CRAN (R 3.5.0)                
    ##  dplyr       * 0.7.6   2018-06-29 [1] CRAN (R 3.5.1)                
    ##  evaluate      0.10.1  2017-06-24 [1] CRAN (R 3.5.0)                
    ##  forcats     * 0.3.0   2018-02-19 [1] CRAN (R 3.5.0)                
    ##  fs            1.2.6   2018-08-23 [1] CRAN (R 3.5.0)                
    ##  ggplot2     * 3.0.0   2018-07-03 [1] CRAN (R 3.5.0)                
    ##  glue          1.2.0   2017-10-29 [1] CRAN (R 3.5.0)                
    ##  gtable        0.2.0   2016-02-26 [1] CRAN (R 3.5.0)                
    ##  haven         1.1.2   2018-06-27 [1] CRAN (R 3.5.0)                
    ##  highr         0.7     2018-06-09 [1] CRAN (R 3.5.0)                
    ##  hms           0.4.2   2018-03-10 [1] CRAN (R 3.5.0)                
    ##  htmltools     0.3.6   2017-04-28 [1] CRAN (R 3.5.0)                
    ##  httr          1.3.1   2017-08-20 [1] CRAN (R 3.5.0)                
    ##  jsonlite      1.5     2017-06-01 [1] CRAN (R 3.5.0)                
    ##  knitr       * 1.20    2018-02-20 [1] CRAN (R 3.5.0)                
    ##  lattice       0.20-35 2017-03-25 [1] CRAN (R 3.5.0)                
    ##  lazyeval      0.2.1   2017-10-29 [1] CRAN (R 3.5.0)                
    ##  lubridate     1.7.4   2018-04-11 [1] CRAN (R 3.5.0)                
    ##  magrittr      1.5     2014-11-22 [1] CRAN (R 3.5.0)                
    ##  memoise       1.1.0   2017-04-21 [1] CRAN (R 3.5.0)                
    ##  modelr        0.1.2   2018-05-11 [1] CRAN (R 3.5.0)                
    ##  munsell       0.5.0   2018-06-12 [1] CRAN (R 3.5.0)                
    ##  nlme          3.1-137 2018-04-07 [1] CRAN (R 3.5.0)                
    ##  pillar        1.2.3   2018-05-25 [1] CRAN (R 3.5.0)                
    ##  pkgbuild      1.0.2   2018-10-16 [1] CRAN (R 3.5.0)                
    ##  pkgconfig     2.0.1   2017-03-21 [1] CRAN (R 3.5.0)                
    ##  pkgload       1.0.2   2018-10-29 [1] CRAN (R 3.5.0)                
    ##  plyr          1.8.4   2016-06-08 [1] CRAN (R 3.5.0)                
    ##  prettyunits   1.0.2   2015-07-13 [1] CRAN (R 3.5.0)                
    ##  processx      3.2.0   2018-08-16 [1] CRAN (R 3.5.0)                
    ##  ps            1.1.0   2018-08-10 [1] CRAN (R 3.5.0)                
    ##  purrr       * 0.2.5   2018-05-29 [1] CRAN (R 3.5.0)                
    ##  R6            2.2.2   2017-06-17 [1] CRAN (R 3.5.0)                
    ##  rcfss       * 0.1.5   2019-04-08 [1] Github (uc-cfss/rcfss@90a1b9d)
    ##  Rcpp          0.12.17 2018-05-18 [1] CRAN (R 3.5.0)                
    ##  readr       * 1.1.1   2017-05-16 [1] CRAN (R 3.5.0)                
    ##  readxl        1.1.0   2018-04-20 [1] CRAN (R 3.5.0)                
    ##  remotes       2.0.2   2018-10-30 [1] CRAN (R 3.5.0)                
    ##  rlang         0.3.0.1 2018-10-25 [1] CRAN (R 3.5.0)                
    ##  rmarkdown     1.10    2018-06-11 [1] CRAN (R 3.5.0)                
    ##  rprojroot     1.3-2   2018-01-03 [1] CRAN (R 3.5.0)                
    ##  rstudioapi    0.8     2018-10-02 [1] CRAN (R 3.5.0)                
    ##  rvest         0.3.2   2016-06-17 [1] CRAN (R 3.5.0)                
    ##  scales        0.5.0   2017-08-24 [1] CRAN (R 3.5.0)                
    ##  sessioninfo   1.1.1   2018-11-05 [1] CRAN (R 3.5.0)                
    ##  stringi       1.2.3   2018-06-12 [1] CRAN (R 3.5.0)                
    ##  stringr     * 1.3.1   2018-05-10 [1] CRAN (R 3.5.0)                
    ##  testthat      2.0.0   2017-12-13 [1] CRAN (R 3.5.0)                
    ##  tibble      * 1.4.2   2018-01-22 [1] CRAN (R 3.5.0)                
    ##  tidyr       * 0.8.1   2018-05-18 [1] CRAN (R 3.5.0)                
    ##  tidyselect    0.2.4   2018-02-26 [1] CRAN (R 3.5.0)                
    ##  tidyverse   * 1.2.1   2017-11-14 [1] CRAN (R 3.5.0)                
    ##  usethis       1.4.0   2018-08-14 [1] CRAN (R 3.5.0)                
    ##  utf8          1.1.4   2018-05-24 [1] CRAN (R 3.5.0)                
    ##  withr         2.1.2   2018-03-15 [1] CRAN (R 3.5.0)                
    ##  xml2          1.2.0   2018-01-24 [1] CRAN (R 3.5.0)                
    ##  yaml          2.1.19  2018-05-01 [1] CRAN (R 3.5.0)                
    ## 
    ## [1] /Library/Frameworks/R.framework/Versions/3.5/Resources/library

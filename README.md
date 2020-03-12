pa\_2
================

## GitHub Documents

This is an R Markdown format used for publishing markdown documents to
GitHub. When you click the **Knit** button all R code chunks are run and
a markdown file (.md) suitable for publishing to GitHub is generated.

`library(tidyverse)`

``` r
library(tidyverse)
Dataframe_1 = read_csv("data/data.csv")
```

``` r
Dataframe_2 = separate(data = Dataframe_1, col = info, into = c("verbo", "acentuacion"), sep = "_") 
Dataframe_2
```

    ## # A tibble: 10 x 5
    ##    verbo acentuacion durationV    f0   int
    ##    <chr> <chr>           <dbl> <dbl> <dbl>
    ##  1 capo  1                0.2  142.   71.0
    ##  2 capo  2                0.17 112.   70.8
    ##  3 pinto 1                0.21 171.   73.7
    ##  4 pinto 2                0.16  94.8  65.6
    ##  5 pujo  1                0.15 164.   81.4
    ##  6 pujo  2                0.12 110.   74.5
    ##  7 quemo 1                0.11 132.   81.5
    ##  8 quemo 2                0.09 106.   75.5
    ##  9 testo 1                0.14 147.   83.4
    ## 10 testo 2                0.1  109.   77.4

``` r
Dataframe_2 %>%
group_by(acentuacion) %>%
summarise(promedio_duracion = mean(durationV), promedio_f0 = mean(f0), promedio_intensidad = mean(int)) 
```

    ## # A tibble: 2 x 4
    ##   acentuacion promedio_duracion promedio_f0 promedio_intensidad
    ##   <chr>                   <dbl>       <dbl>               <dbl>
    ## 1 1                       0.162        151.                78.2
    ## 2 2                       0.128        107.                72.7

``` r
id1 = 1:nrow(Dataframe_2)
ggplot(data = Dataframe_2, aes(x = acentuacion ,y=f0)) + # data, variables, tipo de grafico 
  geom_line() +
  geom_point()
```

![](README_files/figure-gfm/unnamed-chunk-4-1.png)<!-- -->

``` r
id1 = 1:nrow(Dataframe_2)
ggplot(data = Dataframe_2, aes(x = acentuacion ,y=durationV)) + # data, variables, tipo de grafico
  geom_line() +
  geom_point()  
```

![](README_files/figure-gfm/unnamed-chunk-5-1.png)<!-- -->

``` r
id1 = 1:nrow(Dataframe_2)
ggplot(data = Dataframe_2, aes(x = acentuacion ,y=int)) + # data, variables, tipo de grafico
  geom_line() +
  geom_point() 
```

![](README_files/figure-gfm/unnamed-chunk-6-1.png)<!-- -->

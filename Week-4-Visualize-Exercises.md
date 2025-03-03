# Visualize Data
Eli-Wellman

## Your Turn 0

Add a setup chunk that loads the tidyverse packages.

``` r
mpg
```

    # A tibble: 234 × 11
       manufacturer model      displ  year   cyl trans drv     cty   hwy fl    class
       <chr>        <chr>      <dbl> <int> <int> <chr> <chr> <int> <int> <chr> <chr>
     1 audi         a4           1.8  1999     4 auto… f        18    29 p     comp…
     2 audi         a4           1.8  1999     4 manu… f        21    29 p     comp…
     3 audi         a4           2    2008     4 manu… f        20    31 p     comp…
     4 audi         a4           2    2008     4 auto… f        21    30 p     comp…
     5 audi         a4           2.8  1999     6 auto… f        16    26 p     comp…
     6 audi         a4           2.8  1999     6 manu… f        18    26 p     comp…
     7 audi         a4           3.1  2008     6 auto… f        18    27 p     comp…
     8 audi         a4 quattro   1.8  1999     4 manu… 4        18    26 p     comp…
     9 audi         a4 quattro   1.8  1999     4 auto… 4        16    25 p     comp…
    10 audi         a4 quattro   2    2008     4 manu… 4        20    28 p     comp…
    # ℹ 224 more rows

## Your Turn 1

Run the code on the slide to make a graph. Pay strict attention to
spelling, capitalization, and parentheses!

``` r
ggplot(data = mpg) +
  geom_point(mapping = aes(x = displ, y = hwy))
```

![](Week-4-Visualize-Exercises_files/figure-commonmark/unnamed-chunk-3-1.png)

## Your Turn 2

Replace this scatterplot with one that draws boxplots. Use the
cheatsheet. Try your best guess.

``` r
ggplot(data = mpg) +
  geom_boxplot(mapping = aes(x = class, y = hwy))
```

![](Week-4-Visualize-Exercises_files/figure-commonmark/unnamed-chunk-4-1.png)

## Your Turn 3

Make a histogram of the `hwy` variable from `mpg`. Hint: do not supply a
y variable.

``` r
ggplot(data = mpg) +
  geom_histogram(mapping = aes(x = hwy))
```

    `stat_bin()` using `bins = 30`. Pick better value with `binwidth`.

![](Week-4-Visualize-Exercises_files/figure-commonmark/unnamed-chunk-5-1.png)

## Your Turn 4

Use the help page for `geom_histogram` to make the bins 2 units wide.

``` r
ggplot(data = mpg) +
  geom_histogram(mapping = aes(x = hwy), binwidth = 2)
```

![](Week-4-Visualize-Exercises_files/figure-commonmark/unnamed-chunk-6-1.png)

## Your Turn 5

Add `color`, `size`, `alpha`, and `shape` aesthetics to your graph.
Experiment.

``` r
ggplot(data = mpg) +
  geom_point(mapping = aes(x = displ, 
                           y = hwy, 
                           color = class),
                 size = 1,
                 alpha = 0.5)+
  labs(x = "Engine Size Displacement", 
       y = "Highway Mileage (mpg)",
       color = "Class of Vehicle", 
       title = "The Correlation Between Engine Size and Highway Mileage") + 
  theme_light()
```

![](Week-4-Visualize-Exercises_files/figure-commonmark/unnamed-chunk-7-1.png)

## Help Me

What do `facet_grid()` and `facet_wrap()` do? (run the code, interpret,
convince your group)

``` r
# Makes a plot that the commands below will modify
q <- ggplot(mpg) + geom_point(aes(x = displ, y = hwy))

q + facet_grid(. ~ cyl)
```

![](Week-4-Visualize-Exercises_files/figure-commonmark/unnamed-chunk-8-1.png)

``` r
q + facet_grid(drv ~ .)
```

![](Week-4-Visualize-Exercises_files/figure-commonmark/unnamed-chunk-8-2.png)

``` r
q + facet_grid(drv ~ cyl)
```

![](Week-4-Visualize-Exercises_files/figure-commonmark/unnamed-chunk-8-3.png)

``` r
q + facet_wrap(~ class)
```

![](Week-4-Visualize-Exercises_files/figure-commonmark/unnamed-chunk-8-4.png)

## Your Turn 6

Make a bar chart `class` colored by `class`. Use the help page for
`geom_bar` to choose a “color” aesthetic for class.

``` r
ggplot(data = mpg) +
  geom_bar(mapping = aes(x = class, 
                         fill = drv),
           position = "dodge") +
  labs(x = "Class of Vehicle", 
       y = "Number of Vehicles in Sample") + 
  theme_bw()
```

![](Week-4-Visualize-Exercises_files/figure-commonmark/unnamed-chunk-9-1.png)

## Quiz

What will this code do?

``` r
ggplot(mpg, aes(x = displ, y = hwy)) + 
  geom_point(aes(color = class)) +
  geom_smooth(color = "black", 
              se = FALSE,
              method = lm) 
```

    `geom_smooth()` using formula = 'y ~ x'

![](Week-4-Visualize-Exercises_files/figure-commonmark/unnamed-chunk-10-1.png)

``` r
ggsave("example.jpg", width = 6, height = 4)
```

    `geom_smooth()` using formula = 'y ~ x'

------------------------------------------------------------------------

# Take aways

You can use this code template to make thousands of graphs with
**ggplot2**.

``` r
ggplot(data = <DATA>) +
  <GEOM_FUNCTION>(mapping = aes(<MAPPINGS>))
```

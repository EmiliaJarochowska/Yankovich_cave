# Additional information on datasets
Emilia Jarochowska

The original data from Kretzoi (1957) was provided as relative values
(percentages) in a figure. There is information that “some 20 000
fossils of large and small mammals” have been used. So the exercise can
use tables directly extracted from the figure in the paper
(`data/Table2.csv` and `data/Table4.csv`) or absolute counts of fossils,
which students need to transform into relative counts.

To produce the latter, 10 000 fossils was distributed across both
datasets respectively, i.e. voles and non-vole mammals.

``` r
Abs_voles <- sample(1000, dim(Table2)[1], replace = TRUE)
Abs_voles <- round(Abs_voles / sum(Abs_voles) * 1000, 0)
```

``` r
Table2_abs <- Table2

for (i in 1:dim(Table2)[1]) {
  Table2_abs[i,3:10] <- round((Table2[i,3:10]/100) * Abs_voles[i], 0)
}
```

``` r
write.csv(Table2_abs, file="data/Table2_abs.csv")
```

And the same for non-vole mammals:

``` r
Abs_nvoles <- sample(1000, dim(Table4)[1], replace = TRUE)
Abs_nvoles <- round(Abs_nvoles / sum(Abs_nvoles) * 1000, 0)
```

``` r
Table4_abs <- Table4

for (i in 1:dim(Table4)[1]) {
  Table4_abs[i,3:9] <- round((Table4[i,3:9]/100) * Abs_nvoles[i], 0)
}
```

``` r
write.csv2(Table4_abs, file="data/Table4_abs.csv")
```

Now the teacher can decide whether to use the absolute or relative
counts.

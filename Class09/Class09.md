Class09
================

Hands On
--------

``` r
# Save your input data file to a new 'data' directory
fna.data <-  "WisconsinCancer.csv"
```

``` r
# Complete the following code to input the data and store as wisc.df
wisc.df <- read.csv(fna.data)
```

Lets see the first six rows of data

``` r
head(wisc.df)
```

    ##         id diagnosis radius_mean texture_mean perimeter_mean area_mean
    ## 1   842302         M       17.99        10.38         122.80    1001.0
    ## 2   842517         M       20.57        17.77         132.90    1326.0
    ## 3 84300903         M       19.69        21.25         130.00    1203.0
    ## 4 84348301         M       11.42        20.38          77.58     386.1
    ## 5 84358402         M       20.29        14.34         135.10    1297.0
    ## 6   843786         M       12.45        15.70          82.57     477.1
    ##   smoothness_mean compactness_mean concavity_mean concave.points_mean
    ## 1         0.11840          0.27760         0.3001             0.14710
    ## 2         0.08474          0.07864         0.0869             0.07017
    ## 3         0.10960          0.15990         0.1974             0.12790
    ## 4         0.14250          0.28390         0.2414             0.10520
    ## 5         0.10030          0.13280         0.1980             0.10430
    ## 6         0.12780          0.17000         0.1578             0.08089
    ##   symmetry_mean fractal_dimension_mean radius_se texture_se perimeter_se
    ## 1        0.2419                0.07871    1.0950     0.9053        8.589
    ## 2        0.1812                0.05667    0.5435     0.7339        3.398
    ## 3        0.2069                0.05999    0.7456     0.7869        4.585
    ## 4        0.2597                0.09744    0.4956     1.1560        3.445
    ## 5        0.1809                0.05883    0.7572     0.7813        5.438
    ## 6        0.2087                0.07613    0.3345     0.8902        2.217
    ##   area_se smoothness_se compactness_se concavity_se concave.points_se
    ## 1  153.40      0.006399        0.04904      0.05373           0.01587
    ## 2   74.08      0.005225        0.01308      0.01860           0.01340
    ## 3   94.03      0.006150        0.04006      0.03832           0.02058
    ## 4   27.23      0.009110        0.07458      0.05661           0.01867
    ## 5   94.44      0.011490        0.02461      0.05688           0.01885
    ## 6   27.19      0.007510        0.03345      0.03672           0.01137
    ##   symmetry_se fractal_dimension_se radius_worst texture_worst
    ## 1     0.03003             0.006193        25.38         17.33
    ## 2     0.01389             0.003532        24.99         23.41
    ## 3     0.02250             0.004571        23.57         25.53
    ## 4     0.05963             0.009208        14.91         26.50
    ## 5     0.01756             0.005115        22.54         16.67
    ## 6     0.02165             0.005082        15.47         23.75
    ##   perimeter_worst area_worst smoothness_worst compactness_worst
    ## 1          184.60     2019.0           0.1622            0.6656
    ## 2          158.80     1956.0           0.1238            0.1866
    ## 3          152.50     1709.0           0.1444            0.4245
    ## 4           98.87      567.7           0.2098            0.8663
    ## 5          152.20     1575.0           0.1374            0.2050
    ## 6          103.40      741.6           0.1791            0.5249
    ##   concavity_worst concave.points_worst symmetry_worst
    ## 1          0.7119               0.2654         0.4601
    ## 2          0.2416               0.1860         0.2750
    ## 3          0.4504               0.2430         0.3613
    ## 4          0.6869               0.2575         0.6638
    ## 5          0.4000               0.1625         0.2364
    ## 6          0.5355               0.1741         0.3985
    ##   fractal_dimension_worst  X
    ## 1                 0.11890 NA
    ## 2                 0.08902 NA
    ## 3                 0.08758 NA
    ## 4                 0.17300 NA
    ## 5                 0.07678 NA
    ## 6                 0.12440 NA

``` r
#View(wisc.df)
```

How many samples (i.e. patients) are in this data set?

``` r
nrow(wisc.df)
```

    ## [1] 569

Next use as.matrix() to convert the other features (i.e. columns) of the data (in columns 3 through 32) to a matrix. Store this in a variable called wisc.data.

``` r
# Convert the features of the data: wisc.data
wisc.data <- as.matrix(wisc.df[,3:32])
```

Add rownames to our new matric of data

``` r
row.names(wisc.data) <- wisc.df$id
```

Finally, setup a separate new vector called diagnosis to be 1 if a diagnosis is malignant ("M") and 0 otherwise. Note that R coerces TRUE to 1 and FALSE to 0.

``` r
wisc.df$diagnosis
```

    ##   [1] M M M M M M M M M M M M M M M M M M M B B B M M M M M M M M M M M M M
    ##  [36] M M B M M M M M M M M B M B B B B B M M B M M B B B B M B M M B B B B
    ##  [71] M B M M B M B M M B B B M M B M M M B B B M B B M M B B B M M B B B B
    ## [106] M B B M B B B B B B B B M M M B M M B B B M M B M B M M B M M B B M B
    ## [141] B M B B B B M B B B B B B B B B M B B B B M M B M B B M M B B M M B B
    ## [176] B B M B B M M M B M B M B B B M B B M M B M M M M B M M M B M B M B B
    ## [211] M B M M M M B B M M B B B M B B B B B M M B B M B B M M B M B B B B M
    ## [246] B B B B B M B M M M M M M M M M M M M M M B B B B B B M B M B B M B B
    ## [281] M B M M B B B B B B B B B B B B B M B B M B M B B B B B B B B B B B B
    ## [316] B B M B B B M B M B B B B M M M B B B B M B M B M B B B M B B B B B B
    ## [351] B M M M B B B B B B B B B B B M M B M M M B M M B B B B B M B B B B B
    ## [386] M B B B M B B M M B B B B B B M B B B B B B B M B B B B B M B B M B B
    ## [421] B B B B B B B B B B M B M M B M B B B B B M B B M B M B B M B M B B B
    ## [456] B B B B B M M B B B B B B M B B B B B B B B B B M B B B B B B B M B M
    ## [491] B B M B B B B B M M B M B M B B B B B M B B M B M B M M B B B M B B B
    ## [526] B B B B B B B B M B M M B B B B B B B B B B B B B B B B B B B B B B B
    ## [561] B B M M M M M M B
    ## Levels: B M

How many cancer (M) and non cancer samples do we have in our data set?

``` r
 table(wisc.df$diagnosis)
```

    ## 
    ##   B   M 
    ## 357 212

``` r
#diagnosis <- as.numeric(wisc.df$diagnosis)
#tmp <- rep(0, nrow(wisc.df))
diagnosis<- as.numeric(wisc.df$diagnosis == "M")
```

Hands on Questions Q1. How many observations are in this dataset?

``` r
nrow(wisc.data)
```

    ## [1] 569

Q2. How many variables/features in the data are suffixed with \_mean?

``` r
 grep("_mean", colnames(wisc.data))
```

    ##  [1]  1  2  3  4  5  6  7  8  9 10

Q3. How many of the observations have a malignant diagnosis?

``` r
 sum (diagnosis)
```

    ## [1] 212

Section 2
=========

Check the mean and standard deviation of the features (i.e. columns) of the wisc.data to determine if the data should be scaled. Use the colMeans() and apply() functions like you’ve done before.

``` r
# Check column means and standard deviations
 colMeans(wisc.data)
```

    ##             radius_mean            texture_mean          perimeter_mean 
    ##            1.412729e+01            1.928965e+01            9.196903e+01 
    ##               area_mean         smoothness_mean        compactness_mean 
    ##            6.548891e+02            9.636028e-02            1.043410e-01 
    ##          concavity_mean     concave.points_mean           symmetry_mean 
    ##            8.879932e-02            4.891915e-02            1.811619e-01 
    ##  fractal_dimension_mean               radius_se              texture_se 
    ##            6.279761e-02            4.051721e-01            1.216853e+00 
    ##            perimeter_se                 area_se           smoothness_se 
    ##            2.866059e+00            4.033708e+01            7.040979e-03 
    ##          compactness_se            concavity_se       concave.points_se 
    ##            2.547814e-02            3.189372e-02            1.179614e-02 
    ##             symmetry_se    fractal_dimension_se            radius_worst 
    ##            2.054230e-02            3.794904e-03            1.626919e+01 
    ##           texture_worst         perimeter_worst              area_worst 
    ##            2.567722e+01            1.072612e+02            8.805831e+02 
    ##        smoothness_worst       compactness_worst         concavity_worst 
    ##            1.323686e-01            2.542650e-01            2.721885e-01 
    ##    concave.points_worst          symmetry_worst fractal_dimension_worst 
    ##            1.146062e-01            2.900756e-01            8.394582e-02

``` r
 apply(wisc.data,2,sd)
```

    ##             radius_mean            texture_mean          perimeter_mean 
    ##            3.524049e+00            4.301036e+00            2.429898e+01 
    ##               area_mean         smoothness_mean        compactness_mean 
    ##            3.519141e+02            1.406413e-02            5.281276e-02 
    ##          concavity_mean     concave.points_mean           symmetry_mean 
    ##            7.971981e-02            3.880284e-02            2.741428e-02 
    ##  fractal_dimension_mean               radius_se              texture_se 
    ##            7.060363e-03            2.773127e-01            5.516484e-01 
    ##            perimeter_se                 area_se           smoothness_se 
    ##            2.021855e+00            4.549101e+01            3.002518e-03 
    ##          compactness_se            concavity_se       concave.points_se 
    ##            1.790818e-02            3.018606e-02            6.170285e-03 
    ##             symmetry_se    fractal_dimension_se            radius_worst 
    ##            8.266372e-03            2.646071e-03            4.833242e+00 
    ##           texture_worst         perimeter_worst              area_worst 
    ##            6.146258e+00            3.360254e+01            5.693570e+02 
    ##        smoothness_worst       compactness_worst         concavity_worst 
    ##            2.283243e-02            1.573365e-01            2.086243e-01 
    ##    concave.points_worst          symmetry_worst fractal_dimension_worst 
    ##            6.573234e-02            6.186747e-02            1.806127e-02

Now lets do PCA

``` r
# Perform PCA on wisc.data by completing the following code
wisc.pr <- prcomp(wisc.data, scale= TRUE)
summary(wisc.pr)
```

    ## Importance of components:
    ##                           PC1    PC2     PC3     PC4     PC5     PC6
    ## Standard deviation     3.6444 2.3857 1.67867 1.40735 1.28403 1.09880
    ## Proportion of Variance 0.4427 0.1897 0.09393 0.06602 0.05496 0.04025
    ## Cumulative Proportion  0.4427 0.6324 0.72636 0.79239 0.84734 0.88759
    ##                            PC7     PC8    PC9    PC10   PC11    PC12
    ## Standard deviation     0.82172 0.69037 0.6457 0.59219 0.5421 0.51104
    ## Proportion of Variance 0.02251 0.01589 0.0139 0.01169 0.0098 0.00871
    ## Cumulative Proportion  0.91010 0.92598 0.9399 0.95157 0.9614 0.97007
    ##                           PC13    PC14    PC15    PC16    PC17    PC18
    ## Standard deviation     0.49128 0.39624 0.30681 0.28260 0.24372 0.22939
    ## Proportion of Variance 0.00805 0.00523 0.00314 0.00266 0.00198 0.00175
    ## Cumulative Proportion  0.97812 0.98335 0.98649 0.98915 0.99113 0.99288
    ##                           PC19    PC20   PC21    PC22    PC23   PC24
    ## Standard deviation     0.22244 0.17652 0.1731 0.16565 0.15602 0.1344
    ## Proportion of Variance 0.00165 0.00104 0.0010 0.00091 0.00081 0.0006
    ## Cumulative Proportion  0.99453 0.99557 0.9966 0.99749 0.99830 0.9989
    ##                           PC25    PC26    PC27    PC28    PC29    PC30
    ## Standard deviation     0.12442 0.09043 0.08307 0.03987 0.02736 0.01153
    ## Proportion of Variance 0.00052 0.00027 0.00023 0.00005 0.00002 0.00000
    ## Cumulative Proportion  0.99942 0.99969 0.99992 0.99997 1.00000 1.00000

Q4. From your results, what proportion of the original variance is captured by the first principal components (PC1)?

``` r
#looking at the table above 0.4427
```

Q5. How many principal components (PCs) are required to describe at least 70% of the original variance in the data?

you would look at the proportion of variance above and realize you need to sum PC1-PC5 so 5 components

Q6. How many principal components (PCs) are required to describe at least 90% of the original variance in the data?

seven

We need to make our own PCA plot btw 1 is white and 2 is red so +1 gives red

``` r
plot( wisc.pr$x[, 1], wisc.pr$x[,2])
```

![](Class09_files/figure-markdown_github/unnamed-chunk-17-1.png)

``` r
plot(wisc.pr$x[, 1], wisc.pr$x[,2], col=diagnosis+1)
```

![](Class09_files/figure-markdown_github/unnamed-chunk-17-2.png)

``` r
plot(wisc.pr$x[, 1], wisc.pr$x[,2], col=diagnosis+1,
     xlab= "PC1", ylab="PC2")
```

![](Class09_files/figure-markdown_github/unnamed-chunk-17-3.png)

What if we wanted to plot PC1 vs PC3?

``` r
plot(wisc.pr$x[, 1], wisc.pr$x[,3], col=diagnosis+1,
     xlab= "PC1", ylab="PC3")
```

![](Class09_files/figure-markdown_github/unnamed-chunk-18-1.png)

This info is in the $sdev component of our PCA result

``` r
varance <- wisc.pr$sdev^2
# Variance explained by each principal component: pve
pve <- round ( (varance/ sum(varance)) *100,1 )
```

``` r
plot(pve, type= "o")
```

![](Class09_files/figure-markdown_github/unnamed-chunk-20-1.png)

Make the plot a bit fancy :-o

``` r
# Alternative scree plot of the same data, note data driven y-axis
barplot(pve, ylab = "Precent of Variance Explained",
     names.arg=paste0("PC",1:length(pve)), las=2, axes = FALSE)
axis(2, at=pve, labels=round(pve,2)*100 ) 
```

![](Class09_files/figure-markdown_github/unnamed-chunk-21-1.png)

``` r
#axes=false turns of the axes so that you can reset them after in the following line of code
```

Section 3 Hands On \#\# Hierarchial clustering of cancer case data For hierarchial clustering we need a few things 1. Distance matrix **dist()** function 2. The **hclust()** function 3. Use the **cutree()** function to find cluster membership vector

``` r
# Scale the wisc.data data: data.scaled
data.scaled <- scale(wisc.data)
```

``` r
round( apply(wisc.data,2, sd),1)
```

    ##             radius_mean            texture_mean          perimeter_mean 
    ##                     3.5                     4.3                    24.3 
    ##               area_mean         smoothness_mean        compactness_mean 
    ##                   351.9                     0.0                     0.1 
    ##          concavity_mean     concave.points_mean           symmetry_mean 
    ##                     0.1                     0.0                     0.0 
    ##  fractal_dimension_mean               radius_se              texture_se 
    ##                     0.0                     0.3                     0.6 
    ##            perimeter_se                 area_se           smoothness_se 
    ##                     2.0                    45.5                     0.0 
    ##          compactness_se            concavity_se       concave.points_se 
    ##                     0.0                     0.0                     0.0 
    ##             symmetry_se    fractal_dimension_se            radius_worst 
    ##                     0.0                     0.0                     4.8 
    ##           texture_worst         perimeter_worst              area_worst 
    ##                     6.1                    33.6                   569.4 
    ##        smoothness_worst       compactness_worst         concavity_worst 
    ##                     0.0                     0.2                     0.2 
    ##    concave.points_worst          symmetry_worst fractal_dimension_worst 
    ##                     0.1                     0.1                     0.0

``` r
round (apply(data.scaled, 2, sd), 1)
```

    ##             radius_mean            texture_mean          perimeter_mean 
    ##                       1                       1                       1 
    ##               area_mean         smoothness_mean        compactness_mean 
    ##                       1                       1                       1 
    ##          concavity_mean     concave.points_mean           symmetry_mean 
    ##                       1                       1                       1 
    ##  fractal_dimension_mean               radius_se              texture_se 
    ##                       1                       1                       1 
    ##            perimeter_se                 area_se           smoothness_se 
    ##                       1                       1                       1 
    ##          compactness_se            concavity_se       concave.points_se 
    ##                       1                       1                       1 
    ##             symmetry_se    fractal_dimension_se            radius_worst 
    ##                       1                       1                       1 
    ##           texture_worst         perimeter_worst              area_worst 
    ##                       1                       1                       1 
    ##        smoothness_worst       compactness_worst         concavity_worst 
    ##                       1                       1                       1 
    ##    concave.points_worst          symmetry_worst fractal_dimension_worst 
    ##                       1                       1                       1

Calculate the (Euclidean) distances between all pairs of observations in the new scaled dataset and assign the result to data.dist.

``` r
data.dist <- dist(data.scaled)
```

Create a hierarchical clustering model using complete linkage. Manually specify the method argument to hclust() and assign the results to wisc.hclust.

``` r
wisc.hclust <- hclust(data.dist, method= "complete" )
wisc.hclust
```

    ## 
    ## Call:
    ## hclust(d = data.dist, method = "complete")
    ## 
    ## Cluster method   : complete 
    ## Distance         : euclidean 
    ## Number of objects: 569

``` r
plot(wisc.hclust)
```

![](Class09_files/figure-markdown_github/unnamed-chunk-27-1.png)

Q11. Using the plot() and abline() functions, what is the height at which the clustering model has 4 clusters? Hide

``` r
 wisc.pr.hclust <- plot(wisc.hclust)
h <- "height"
abline(h=19, col="red", lty=2)
```

![](Class09_files/figure-markdown_github/unnamed-chunk-28-1.png) Use cutree() to cut the tree so that it has 4 clusters. Assign the output to the variable wisc.hclust.clusters.

Section 5 \#\# Cluster in PCA space

we need 1. distance matrix 2. clustering function 3. cutree

This was our PCA resut of PC1 vs Pc2

``` r
plot(wisc.pr$x[, 1], wisc.pr$x[,2], col=diagnosis+1,
     xlab= "PC1", ylab="PC2")
```

![](Class09_files/figure-markdown_github/unnamed-chunk-29-1.png)

``` r
pc.dist <- dist(wisc.pr$x[,1:2])
pc.hclust <- hclust(pc.dist, method="ward.D2")
plot(pc.hclust)
```

![](Class09_files/figure-markdown_github/unnamed-chunk-30-1.png)

``` r
grps3 <- cutree(pc.hclust, k=3, h= 19)
grps3
```

    ##    842302    842517  84300903  84348301  84358402    843786    844359 
    ##         1         1         1         2         1         2         1 
    ##  84458202    844981  84501001    845636  84610002    846226    846381 
    ##         2         2         2         3         2         1         3 
    ##  84667401  84799002    848406  84862001    849014   8510426   8510653 
    ##         2         2         1         2         1         3         3 
    ##   8510824   8511133    851509    852552    852631    852763    852781 
    ##         3         2         1         1         2         2         1 
    ##    852973    853201    853401    853612  85382601    854002    854039 
    ##         2         1         1         2         2         1         2 
    ##    854253    854268    854941    855133    855138    855167    855563 
    ##         2         3         3         3         3         3         3 
    ##    855625    856106  85638502    857010  85713702     85715    857155 
    ##         1         3         3         1         3         2         3 
    ##    857156    857343    857373    857374    857392    857438  85759902 
    ##         3         3         3         3         1         3         3 
    ##    857637    857793    857810    858477    858970    858981    858986 
    ##         1         2         3         3         3         3         2 
    ##    859196  85922302    859283    859464    859465    859471    859487 
    ##         3         2         2         3         3         2         3 
    ##    859575    859711    859717    859983   8610175   8610404   8610629 
    ##         1         2         2         3         3         1         3 
    ##   8610637   8610862   8610908    861103   8611161   8611555   8611792 
    ##         2         1         3         3         2         1         2 
    ##   8612080   8612399  86135501  86135502    861597    861598    861648 
    ##         3         1         3         1         3         3         3 
    ##    861799    861853    862009    862028     86208     86211    862261 
    ##         3         3         3         2         1         3         3 
    ##    862485    862548    862717    862722    862965    862980    862989 
    ##         3         3         3         3         3         3         3 
    ##    863030    863031    863270     86355    864018    864033     86408 
    ##         2         3         3         1         3         3         3 
    ##     86409    864292    864496    864685    864726    864729    864877 
    ##         2         3         3         3         3         2         2 
    ##    865128    865137     86517    865423    865432    865468     86561 
    ##         1         3         1         1         3         3         3 
    ##    866083    866203    866458    866674    866714      8670  86730502 
    ##         3         1         2         1         3         1         1 
    ##    867387    867739    868202    868223    868682    868826    868871 
    ##         3         1         3         3         3         2         3 
    ##    868999    869104    869218    869224    869254    869476    869691 
    ##         3         1         3         3         3         3         2 
    ##  86973701  86973702    869931 871001501 871001502   8710441     87106 
    ##         3         3         3         3         2         2         3 
    ##   8711002   8711003   8711202   8711216    871122    871149   8711561 
    ##         3         3         2         3         3         3         3 
    ##   8711803    871201   8712064   8712289   8712291     87127   8712729 
    ##         1         1         3         1         3         3         1 
    ##   8712766   8712853  87139402     87163     87164    871641    871642 
    ##         1         3         3         3         2         3         3 
    ##    872113    872608  87281702    873357    873586    873592    873593 
    ##         3         2         2         3         3         1         1 
    ##    873701    873843    873885    874158    874217    874373    874662 
    ##         1         3         3         3         3         3         3 
    ##    874839    874858    875093    875099    875263  87556202    875878 
    ##         3         2         3         3         2         2         3 
    ##    875938    877159    877486    877500    877501    877989    878796 
    ##         2         1         1         3         3         1         1 
    ##     87880     87930    879523    879804    879830   8810158   8810436 
    ##         2         3         3         3         3         3         3 
    ## 881046502   8810528   8810703 881094802   8810955   8810987   8811523 
    ##         1         3         1         2         2         2         3 
    ##   8811779   8811842  88119002   8812816   8812818   8812844   8812877 
    ##         3         1         1         3         3         3         2 
    ##   8813129  88143502  88147101  88147102  88147202    881861    881972 
    ##         3         3         3         3         3         2         2 
    ##  88199202  88203002  88206102    882488  88249602  88299702    883263 
    ##         3         3         1         3         3         1         1 
    ##    883270  88330202  88350402    883539    883852  88411702    884180 
    ##         3         1         3         3         2         3         1 
    ##    884437    884448    884626  88466802    884689    884948  88518501 
    ##         3         3         2         3         3         1         3 
    ##    885429   8860702    886226    886452  88649001    886776    887181 
    ##         1         1         1         3         1         2         1 
    ##  88725602    887549    888264    888570    889403    889719  88995002 
    ##         2         1         3         1         3         1         1 
    ##   8910251   8910499   8910506   8910720   8910721   8910748   8910988 
    ##         3         3         3         3         3         3         1 
    ##   8910996   8911163   8911164   8911230   8911670   8911800   8911834 
    ##         3         3         3         3         3         3         3 
    ##   8912049   8912055     89122   8912280   8912284   8912521   8912909 
    ##         1         3         1         2         3         3         3 
    ##      8913   8913049  89143601  89143602      8915    891670    891703 
    ##         3         3         3         2         3         3         3 
    ##    891716    891923    891936    892189    892214    892399    892438 
    ##         3         3         3         3         3         3         1 
    ##    892604  89263202    892657     89296    893061     89344     89346 
    ##         3         1         3         3         3         3         3 
    ##    893526    893548    893783  89382601  89382602    893988    894047 
    ##         3         3         3         3         3         3         3 
    ##    894089    894090    894326    894329    894335    894604    894618 
    ##         3         3         1         2         3         3         1 
    ##    894855    895100  89511501  89511502     89524    895299   8953902 
    ##         3         1         3         3         3         3         2 
    ##    895633    896839    896864    897132    897137    897374  89742801 
    ##         2         2         3         3         3         3         1 
    ##    897604    897630    897880     89812     89813    898143     89827 
    ##         3         1         3         1         3         3         3 
    ##    898431  89864002    898677    898678     89869    898690    899147 
    ##         1         3         3         3         3         3         3 
    ##    899187    899667    899987   9010018    901011   9010258   9010259 
    ##         3         2         1         2         3         3         3 
    ##    901028   9010333 901034301 901034302    901041   9010598   9010872 
    ##         3         3         3         3         3         3         3 
    ##   9010877    901088   9011494   9011495   9011971   9012000   9012315 
    ##         3         1         1         3         1         1         2 
    ##   9012568   9012795    901288   9013005    901303    901315   9013579 
    ##         3         1         1         3         3         2         3 
    ##   9013594   9013838    901549    901836     90250     90251    902727 
    ##         3         2         3         3         3         3         3 
    ##     90291    902975    902976    903011     90312  90317302    903483 
    ##         3         3         3         3         2         3         3 
    ##    903507    903516    903554    903811  90401601  90401602    904302 
    ##         2         1         3         3         3         3         3 
    ##    904357  90439701    904647    904689      9047    904969    904971 
    ##         3         2         3         3         3         3         3 
    ##    905189    905190  90524101    905501    905502    905520    905539 
    ##         3         3         1         3         3         3         3 
    ##    905557    905680    905686    905978  90602302    906024    906290 
    ##         3         3         3         3         1         3         3 
    ##    906539    906564    906616    906878    907145    907367    907409 
    ##         3         2         3         3         3         3         3 
    ##     90745  90769601  90769602    907914    907915    908194    908445 
    ##         3         3         3         2         3         1         1 
    ##    908469    908489    908916    909220    909231    909410    909411 
    ##         3         3         3         3         3         3         3 
    ##    909445  90944601    909777   9110127   9110720   9110732   9110944 
    ##         1         3         3         1         3         1         3 
    ##    911150 911157302   9111596   9111805   9111843    911201    911202 
    ##         3         1         3         1         3         3         3 
    ##   9112085   9112366   9112367   9112594   9112712 911296201 911296202 
    ##         3         3         3         3         3         1         1 
    ##   9113156 911320501 911320502   9113239   9113455   9113514   9113538 
    ##         3         3         3         2         3         3         2 
    ##    911366   9113778   9113816    911384   9113846    911391    911408 
    ##         3         3         3         3         3         3         3 
    ##    911654    911673    911685    911916    912193     91227    912519 
    ##         3         3         3         2         3         3         3 
    ##    912558    912600    913063    913102    913505    913512    913535 
    ##         3         3         2         3         1         3         3 
    ##  91376701  91376702    914062    914101    914102    914333    914366 
    ##         3         3         1         3         3         3         3 
    ##    914580    914769     91485    914862     91504     91505    915143 
    ##         3         1         1         3         2         3         1 
    ##    915186    915276  91544001  91544002    915452    915460     91550 
    ##         2         2         3         3         3         2         3 
    ##    915664    915691    915940  91594602    916221    916799    916838 
    ##         3         2         3         3         3         1         1 
    ##    917062    917080    917092  91762702     91789    917896    917897 
    ##         3         3         3         1         3         3         3 
    ##     91805  91813701  91813702    918192    918465     91858  91903901 
    ##         3         3         3         3         3         3         3 
    ##  91903902  91930402    919537    919555  91979701    919812    921092 
    ##         3         1         3         1         3         3         3 
    ##    921362    921385    921386    921644    922296    922297    922576 
    ##         3         3         3         3         3         3         3 
    ##    922577    922840    923169    923465    923748    923780    924084 
    ##         3         3         3         3         3         3         3 
    ##    924342    924632    924934    924964    925236    925277    925291 
    ##         3         3         3         3         3         3         3 
    ##    925292    925311    925622    926125    926424    926682    926954 
    ##         3         3         2         1         1         1         1 
    ##    927241     92751 
    ##         1         3

``` r
#how many in each cluster
table(grps3)
```

    ## grps3
    ##   1   2   3 
    ## 112  83 374

``` r
table(grps3, diagnosis)
```

    ##      diagnosis
    ## grps3   0   1
    ##     1   0 112
    ##     2  18  65
    ##     3 339  35

Section 7

``` r
#url <- "new_samples.csv"
url <- "https://tinyurl.com/new-samples-CSV"
new <- read.csv(url)
npc <- predict(wisc.pr, newdata=new)
npc
```

    ##            PC1       PC2        PC3        PC4       PC5        PC6
    ## [1,]  2.576616 -3.135913  1.3990492 -0.7631950  2.781648 -0.8150185
    ## [2,] -4.754928 -3.009033 -0.1660946 -0.6052952 -1.140698 -1.2189945
    ##             PC7        PC8       PC9       PC10      PC11      PC12
    ## [1,] -0.3959098 -0.2307350 0.1029569 -0.9272861 0.3411457  0.375921
    ## [2,]  0.8193031 -0.3307423 0.5281896 -0.4855301 0.7173233 -1.185917
    ##           PC13     PC14      PC15       PC16        PC17        PC18
    ## [1,] 0.1610764 1.187882 0.3216974 -0.1743616 -0.07875393 -0.11207028
    ## [2,] 0.5893856 0.303029 0.1299153  0.1448061 -0.40509706  0.06565549
    ##             PC19       PC20       PC21       PC22       PC23       PC24
    ## [1,] -0.08802955 -0.2495216  0.1228233 0.09358453 0.08347651  0.1223396
    ## [2,]  0.25591230 -0.4289500 -0.1224776 0.01732146 0.06316631 -0.2338618
    ##             PC25         PC26         PC27        PC28         PC29
    ## [1,]  0.02124121  0.078884581  0.220199544 -0.02946023 -0.015620933
    ## [2,] -0.20755948 -0.009833238 -0.001134152  0.09638361  0.002795349
    ##              PC30
    ## [1,]  0.005269029
    ## [2,] -0.019015820

The 2 blue points are 2 new patients, new data recorded as part of the new data set above

``` r
plot(wisc.pr$x[,1:2], col=diagnosis + 1)
points(npc[,1], npc[,2], col="blue", pch=15, cex=3)
```

![](Class09_files/figure-markdown_github/unnamed-chunk-35-1.png)

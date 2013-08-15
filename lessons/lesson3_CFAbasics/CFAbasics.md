Confirmatory Factor Analysis: Basics
========================================================

## Basic CFA in Lavaan





```r
hs.model <- "\nvisual  =~ x1 + x2 + x3\ntextual =~ x4 + x5 + x6\nspeed   =~ x7 + x8 + x9\n"
lfit <- cfa(hs.model, data = df)
summary(lfit, fit.measures = TRUE, rsquare = TRUE)
```

lavaan (0.5-13) converged normally after  35 iterations

  Number of observations                           301

  Estimator                                         ML
  Minimum Function Test Statistic               85.306
  Degrees of freedom                                24
  P-value (Chi-square)                           0.000

Model test baseline model:

  Minimum Function Test Statistic              918.852
  Degrees of freedom                                36
  P-value                                        0.000

Full model versus baseline model:

  Comparative Fit Index (CFI)                    0.931
  Tucker-Lewis Index (TLI)                       0.896

Loglikelihood and Information Criteria:

  Loglikelihood user model (H0)              -3737.745
  Loglikelihood unrestricted model (H1)      -3695.092

  Number of free parameters                         21
  Akaike (AIC)                                7517.490
  Bayesian (BIC)                              7595.339
  Sample-size adjusted Bayesian (BIC)         7528.739

Root Mean Square Error of Approximation:

  RMSEA                                          0.092
  90 Percent Confidence Interval          0.071  0.114
  P-value RMSEA <= 0.05                          0.001

Standardized Root Mean Square Residual:

  SRMR                                           0.065

Parameter estimates:

  Information                                 Expected
  Standard Errors                             Standard

                   Estimate  Std.err  Z-value  P(>|z|)
Latent variables:
  visual =~
    x1                1.000
    x2                0.554    0.100    5.554    0.000
    x3                0.729    0.109    6.685    0.000
  textual =~
    x4                1.000
    x5                1.113    0.065   17.014    0.000
    x6                0.926    0.055   16.703    0.000
  speed =~
    x7                1.000
    x8                1.180    0.165    7.152    0.000
    x9                1.082    0.151    7.155    0.000

Covariances:
  visual ~~
    textual           0.408    0.074    5.552    0.000
    speed             0.262    0.056    4.660    0.000
  textual ~~
    speed             0.173    0.049    3.518    0.000

Variances:
    x1                0.549    0.114
    x2                1.134    0.102
    x3                0.844    0.091
    x4                0.371    0.048
    x5                0.446    0.058
    x6                0.356    0.043
    x7                0.799    0.081
    x8                0.488    0.074
    x9                0.566    0.071
    visual            0.809    0.145
    textual           0.979    0.112
    speed             0.384    0.086

R-Square:

    x1                0.596
    x2                0.179
    x3                0.338
    x4                0.725
    x5                0.731
    x6                0.702
    x7                0.324
    x8                0.523
    x9                0.442


## Basic CFA in Mplus


```r
hs.mpob <- mplusObject(TITLE = "basic mplus CFA", MODEL = "visual  by x1 x2 x3;\ntextual by x4 x5 x6;\nspeed   by x7 x8 x9;", 
    usevariables = c("x1", "x2", "x3", "x4", "x5", "x6", "x7", "x8", "x9"), 
    rdata = df)
mpcfa <- mplusModeler(hs.mpob, dataout = "mpcfa.dat", modelout = "mpcfa.inp", 
    run = 1L)
```

```
## Wrote model to: mpcfa.inp
```

```
## Wrote data to: mpcfa.dat
```

```
## Warning: The file 'mpcfa.dat' currently exists and will be overwritten
```


Running model: mpcfa.inp 
System command: cd "/home/wmmurrah/RStudioProjects/Rtutorials/IntroFactorAnalysis/lessons/lesson3_CFAbasics" && "mplus" "mpcfa.inp" 
Reading model:  mpcfa.out 

```r
ms <- extractModelSummaries(mpcfa)
```

```
## Error: invalid 'file' argument
```

```r
LatexSummaryTable(ms)
```

```
## Error: object 'ms' not found
```


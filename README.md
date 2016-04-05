# emov

[![CRAN version](http://www.r-pkg.org/badges/version/emov)](http://cran.r-project.org/package=emov)

An R package for fixation and saccade detection in eye tracking recordings. Eye movements consist of alternating saccades and fixations. This package implements a dispersion-based algorithm (I-DT) proposed by Salvucci & Goldberg (2000) and detects fixations in the first place, compared to the velocity threshold algorithms which detect saccades.

## Install from CRAN
    install.packages("emov")

## Manual installation
    unzip emov-master.zip
    mv emov-master emov
    R --vanilla CMD INSTALL --build emov

## Getting started: Running the Demo
    library("emov")
    demo(fivesec, package="emov")
    ?emov.idt
    
![alt tag](/inst/images/plot.png)

## Getting started: An Example
    library("emov")
    data(fivesec)

Low pass filtering of the data:

    fivesec$x = filter(fivesec$x, rep(1/3, 3))
    fivesec$y = filter(fivesec$y, rep(1/3, 3))

Fixation detection with a dispersion of 2 cm, and a minimal fixation duration of 20 samples (corresponds to 100 ms, 200 Hz tracker). In the sample data, 2 cm at a viewing distance of 80 cm corresponds to 1.43 degrees.

    emov.angdia(2, 80)
    fixations = emov.idt(fivesec$time, fivesec$x, fivesec$y, 2, 20)
       start   end   dur           x          y
    1  0.000 0.275 0.275   0.4417061  -7.288781
    2  0.285 0.460 0.175   3.4010389  -7.564090
    3  0.485 0.705 0.220   9.9452156  -7.369493
    4  0.715 0.900 0.185   6.4235088  -7.560851
    5  0.945 1.175 0.230  19.1238156  -7.768803
    6  1.190 1.355 0.165  23.4139510  -7.589660
    7  1.445 1.630 0.185  26.7930263  -7.301396
    8  1.645 2.005 0.360  30.2128219  -6.922623
    9  2.220 2.465 0.245 -18.0343467 -10.677866
    10 2.475 2.790 0.315 -17.1090937 -10.375125
    11 2.810 3.205 0.395 -10.2890283  -9.988374
    12 3.245 3.530 0.285   1.0143391 -10.091091
    13 3.545 3.875 0.330  -2.5099814 -10.060751
    14 3.915 4.390 0.475   7.7836712 -10.367486
    15 4.450 4.600 0.150  18.6530860  -9.983666
    16 4.625 4.875 0.250  24.1802288 -10.188763

## Update package to newest CRAN version
    packageVersion("emov")
    detach("package:emov", unload=TRUE)
    install.packages("emov")
    library("emov")
    packageVersion("emov")

## Unload package
    detach("package:emov", unload=TRUE)

## Uninstall package
    R --vanilla CMD REMOVE emov

## Reference
Salvucci, D. D., & Goldberg, J. H. (2000). Identifying fixations and saccades in eye-tracking pro-
tocols. In Proceedings of the 2000 symposium on eye tracking research & applications (pp. 71-78).
New York: ACM.

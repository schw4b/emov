# emov
An R package for fixation and saccade detection in eye movement recordings. Eye movements consist of alternating saccades and fixations. This package implements a dispersion-based algorithm (I-DT) proposed by Salvucci & Goldberg (2000) and detects fixations in the first place, compared to the velocity threshold algorithms which detect saccades.

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

## Getting started: An Example
    library("emov")
    data(fivesec)
Low pass filtering of the data:
    fivesec$x = filter(fivesec$x, rep(1/3, 3))
    fivesec$y = filter(fivesec$y, rep(1/3, 3))
Fixation detection with a dispersion of 2cm, and 20 samples (100 ms, 200 Hz tracker).
In the sample data, 2 cm corresponds to 1.43 degrees at a viewing distance of 80 cm.
    emov.angdia(2, 80)
    fixations = emov.idt(fivesec$time, fivesec$x, fivesec$y, 2, 20)

## Unload package
    detach("package:emov", unload=TRUE)

## Uninstall package
    R --vanilla CMD REMOVE emov

## Reference
Salvucci, D. D., & Goldberg, J. H. (2000). Identifying fixations and saccades in eye-tracking pro-
tocols. In Proceedings of the 2000 symposium on eye tracking research & applications (pp. 71-78).
New York: ACM.

![alt tag](/inst/images/plot.png)

# emov
An R package for fixation and saccade detection in eye movement recordings. Eye movements consist of alternating saccades and fixations. This package implements a dispersion-based algorithm (I-DT) proposed by Salvucci & Goldberg (2000) and detects fixations in the first place, compared to the velocity threshold algorithms which detect saccades.

Manual installaton:
    sudo R CMD INSTALL saccades_0.1.tar.gz
  
Getting started:
    library("emov")
    demo(fivesec, package="emov")
    ?emov.idt

Reference:
Salvucci, D. D., & Goldberg, J. H. (2000). Identifying fixations and saccades in eye-tracking pro-
tocols. In Proceedings of the 2000 symposium on eye tracking research & applications (pp. 71-78).
New York: ACM.

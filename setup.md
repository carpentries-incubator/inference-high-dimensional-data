---
title: Setup
---

## Data Files and Project Organization

1. Make a new folder in your Desktop called `inference`. Move into this new 
   folder.

2. Create  a `data` folder to hold the data, a `scripts` folder to house your 
   scripts, and a `results` folder to hold results. 

    Alternatively, you can use the R console to run the following commands for 
    steps 1 and 2.

    ~~~
    setwd("~/Desktop")
    dir.create("./inference")
    setwd("~/Desktop/inference")
    dir.create("./data")
    dir.create("./scripts")
    dir.create("./results")
    ~~~

3. Please download the following files and place it in your `data` folder. You 
can copy and paste the following into the R console to download the data.

~~~
download.file(url = "https://raw.githubusercontent.com/genomicsclass/dagdata/master/inst/extdata/femaleControlsPopulation.csv", 
              destfile = "data/femaleControlsPopulation.csv", 
              mode = "wb")
download.file(url = "https://github.com/genomicsclass/GSE5859/raw/refs/heads/master/data/GSE5859.rda",
              destfile = "data/GSE5859.rda",
              mode = "wb")
download.file(url = "https://github.com/genomicsclass/GSE5859Subset/raw/refs/heads/master/data/GSE5859Subset.rda",
              destfile = "data/GSE5859Subset.rda",
              mode = "wb")
download.file(url = "https://github.com/genomicsclass/maPooling/raw/refs/heads/master/data/maPooling.RData",
              destfile = "data/maPooling.RData",
              mode = "wb")
download.file(url = "https://github.com/genomicsclass/tissuesGeneExpression/raw/refs/heads/master/data/tissuesGeneExpression.rda",
              destfile = "data/tissuesGeneExpression.rda",
              mode = "wb")
~~~

## Software Setup

R is a programming language that is especially powerful for data exploration, 
visualization, and statistical analysis. To interact with R, we use RStudio. 

1. Install the latest version of R from [CRAN](https://cran.r-project.org/). 
If you are using a JAX-owned machine, you can use the JAX Self Service app 
instead without needing support from the IT help desk.

2. Install the latest version of RStudio 
[here](https://www.rstudio.com/products/rstudio/download/). Choose the free 
RStudio Desktop version for Windows, Mac, or Linux. If you are using a 
JAX-owned machine, you can use the JAX Self Service app instead without needing 
support from the IT help desk.

3. Start RStudio. We will use several packages from CRAN. You can install them 
from the Console or from the Install button on the RStudio Packages tab. 
Copy-paste this list of packages into the Install dialog box: 

    `devtools, BiocManager, here, rafalib, lasso2, matrixStats`

    Alternatively, run the following in the Console.

    ~~~
    install.packages(c("BiocManager", "here", 
                       "rafalib", "matrixStats", "Brq"))
    ~~~

 4. Once you have installed the packages, load the libraries by checking the box 
next to each package name on the Packages tab, or alternatively running this 
code in the Console for each package.

    ~~~
    library(BiocManager)
    library(here)
    library(rafalib)
    library(matrixStats)
    ~~~
    

5. Install these  Bioconductor packages by running the code in the Console:

    ~~~
    BiocManager::install(c("genefilter", "SpikeInSubset", 
                           "SummarizedExperiment", "parathyroidSE", "Biobase", 
                           "limma", "qvalue", "PCAtools"))
    ~~~

6. Once you have installed the Bioconductor packages, load the libraries by 
running this code in the Console.

    ~~~
    library(genefilter)
    library(SpikeInSubset)
    library(SummarizedExperiment)
    library(parathyroidSE)
    library(Biobase)
    library(limma)
    library(qvalue)
    library(PCAtools)
    ~~~

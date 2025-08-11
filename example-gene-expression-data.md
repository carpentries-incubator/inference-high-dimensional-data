---
title: Example Gene Expression Datasets
teaching: 15
exercises: 20
source: Rmd
---

::::::::::::::::::::::::::::::::::::::: objectives

- Explore a high-throughput dataset composed of three tables.
- Examine the features (high-throughput measurements) of the data you explored.

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: questions

- What data will be be using for our analyses?

::::::::::::::::::::::::::::::::::::::::::::::::::



# Explore a Gene Expression Dataset

Since there is a vast number of available public datasets, we use several gene 
expression examples. Nonetheless, the statistical techniques you will learn have 
also proven useful in other fields that make use of high-throughput technologies. 
Technologies such as microarrays, next generation sequencing, fMRI, and mass 
spectrometry all produce data to answer questions for which what we learn here 
will be indispensable. 

#### The three tables

Most of the data we use as examples in this book are created with 
high-throughput technologies. These technologies measure thousands of _features_. 
Examples of features are genes, single base locations of the genome, genomic 
regions, or image pixel intensities. Each specific measurement product is 
defined by a specific set of features. For example, a specific gene expression 
microarray product is defined by the set of genes that it measures. 

A specific study will typically use one product to make measurements on several 
experimental units, such as individuals. The most common experimental unit will 
be the individual, but they can also be defined by other entities, for example 
different parts of a tumor. We often call the experimental units _samples_ 
following experimental jargon. It is important that these are not confused with 
samples as referred to in previous chapters, for example "random sample". 

So a high-throughput experiment is usually defined by three tables: one with the 
high-throughput measurements and two tables with information about the columns 
and rows of this first table respectively.

Because a dataset is typically defined by a set of experimental units and a 
product defines a fixed set of features, the high-throughput measurements can be 
stored in an <i>n x m</i> matrix, with <i>n</i> the number of units and <i>m</i> 
the number of features. In R, the convention has been to store the transpose of 
these matrices, in which all the rows become columns and the columns become the 
rows. 

Here is an example from a gene expression dataset:


``` r
load("./data/GSE5859Subset.rda") ## this loads the three tables
dim(geneExpression)
```

``` output
[1] 8793   24
```

We have RNA expression measurements for 8793 genes from blood taken from 24 
individuals (the experimental units). For most statistical analyses, we will 
also need information about the individuals. For example, in this case the data 
was originally collected to compare gene expression across ethnic groups. 
However, we have created a subset of this dataset for illustration and separated 
the data into two groups:


``` r
dim(sampleInfo)
```

``` output
[1] 24  4
```

``` r
head(sampleInfo)
```

``` output
    ethnicity       date         filename group
107       ASN 2005-06-23 GSM136508.CEL.gz     1
122       ASN 2005-06-27 GSM136530.CEL.gz     1
113       ASN 2005-06-27 GSM136517.CEL.gz     1
163       ASN 2005-10-28 GSM136576.CEL.gz     1
153       ASN 2005-10-07 GSM136566.CEL.gz     1
161       ASN 2005-10-07 GSM136574.CEL.gz     1
```

``` r
sampleInfo$group
```

``` output
 [1] 1 1 1 1 1 1 1 1 1 1 1 1 0 0 0 0 0 0 0 0 0 0 0 0
```

One of the columns, filenames, permits us to connect the rows of this table to 
the columns of the measurement table.


``` r
match(sampleInfo$filename, colnames(geneExpression))
```

``` output
 [1]  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24
```


Finally, we have a table describing the features:


``` r
dim(geneAnnotation)
```

``` output
[1] 8793    4
```

``` r
head(geneAnnotation)
```

``` output
     PROBEID  CHR     CHRLOC SYMBOL
1  1007_s_at chr6   30852327   DDR1
30   1053_at chr7  -73645832   RFC2
31    117_at chr1  161494036  HSPA6
32    121_at chr2 -113973574   PAX8
33 1255_g_at chr6   42123144 GUCA1A
34   1294_at chr3  -49842638   UBA7
```

The table includes an ID that permits us to connect the rows of this table with 
the rows of the measurement table:


``` r
head(match(geneAnnotation$PROBEID, rownames(geneExpression)))
```

``` output
[1] 1 2 3 4 5 6
```

The table also includes biological information about the features, namely 
chromosome location and the gene "name" used by biologists.

::::::::::::::::::::::::::::::::::::: challenge

## Exercise 1: How many samples were processed on 2005-06-27?

:::::::::::::::: solution

~~~
unique(sampleInfo$date) # check date format
sampleInfo[sampleInfo$date == "2005-06-27",]  
sum(sampleInfo$date == "2005-06-27") # sum of TRUEs     
~~~

:::::::::::::::::::::::::

## Exercise 2: How many of the genes represented in this particular technology are on chromosome Y?

:::::::::::::::: solution

~~~
unique(geneAnnotation$CHR) # check chromosome spelling  
sum(geneAnnotation$CHR == "chrY", na.rm = TRUE) # remove missing values # (NAs) to sum TRUEs
~~~
:::::::::::::::::::::::::

## Exercise 3: What is the log expression value for gene ARPC1A on the one subject that we measured on 2005-06-10?

:::::::::::::::: solution

~~~
sampleInfo[sampleInfo$date == "2005-06-10",] # June 10 sample 
sampleFileName <- sampleInfo[sampleInfo$date == "2005-06-10", "filename"] # save file name   
sampleProbeID <- geneAnnotation[which(geneAnnotation$SYMBOL == "ARPC1A"), "PROBEID"] # save probe ID
geneExpression[sampleProbeID, sampleFileName]
~~~
:::::::::::::::::::::::::


:::::::::::::::::::::::::::::::::::::::::::::::

::::::::::::::::::::::::::::::::::::: challenge

## Discussion
What kinds of research questions might you ask of this data?
What are the dependent (response) and independent variables?
Turn to a partner and discuss, then share with the group in the collaborative
document.

:::::::::::::::: solution

:::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: keypoints

- High-throughput data measures thousands of features.
- High-throughput data is typically composed of multiple tables.

::::::::::::::::::::::::::::::::::::::::::::::::::

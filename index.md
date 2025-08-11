---
site: sandpaper::sandpaper_site
---

High-throughput technologies have changed basic biology and the biomedical 
sciences from data poor disciplines to data intensive ones. A specific example 
comes from research fields interested in understanding gene expression. Gene 
expression is the process in which DNA, the blueprint for life, is copied into 
RNA, the templates for the synthesis of proteins, the building blocks for life. 
In the 1990s, the analysis of gene expression data amounted to spotting black 
dots on a piece of paper or extracting a few numbers from standard curves. With 
high-throughput technologies, such as microarrays, this suddenly changed to 
sifting through tens of thousands of numbers. More recently, RNA sequencing has 
further increased data complexity. Biologists went from using their eyes or 
simple summaries to categorize results, to having thousands (and now millions) 
of measurements per sample to analyze. In this lesson we will focus on 
statistical inference in the context of high-throughput measurements. 
Specifically, we focus on the problem of detecting differences in groups using 
statistical tests and quantifying uncertainty in a meaningful way. We also 
introduce exploratory data analysis techniques that should be used in 
conjunction with inference when analyzing high-throughput data.

This lesson presents data analysis concepts featured in 
[*Data Analysis for the Life Sciences*](https://leanpub.com/dataanalysisforthelifesciences)
by Rafael A. Irizarry and Michael I. Love. The lesson is adapted from software
for chapters on
[Inference for High-Dimensional Data](https://github.com/genomicsclass/labs/tree/master/advinference),
[Statistical Modeling](https://github.com/genomicsclass/labs/tree/master/modeling) and 
[Distance and Dimension Reduction](https://github.com/genomicsclass/labs/tree/master/highdim)
which are published under 
[this MIT license](https://github.com/genomicsclass/labs?tab=MIT-1-ov-file).
Adaptation was funded by NIH grant 1R25GM141520 awarded to Dr. Gary Churchill at
The Jackson Laboratory.

::: callout
This lesson assumes basic skills in the R statistical programming language.
If you know how install packages, load libraries and data, and work with common 
R data structures (e.g. vectors, data frames, matrices) you are ready for this
course.
:::

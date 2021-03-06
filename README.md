## Welcome to Miko's pathway analysis with GSEA!

### A brief introduction of GSEA:

*What is it?*

A method that answers the question of whether a set of biologically relevant genes (e.g. a pathway) correlates with a phenotype.

*Why is it important?*

1. Unveil the relationship between genes in pathways and genes differentially expressed in a disease
2. Can determine if pathways are upregulated or downregulated
3. Part of network analysis workflow

*How does it work?*

Implemented in Jupyter Notebook with GSEApy package

*Method of GSEA:*

1. Calculate enrichment score (ES):
the degree of the gene set being over-represented at extremes of L

2. Estimate statistical significance (False discovery rate):
If FDR < 0.3, this gene set is significant in the enrichment
(How to Determine the significant pathway)

3. Adjust for multiple hypothesis testing:
Calculate normalized enrichment score (NES), etc.

### Motivation:

When running GSEA, I found that each run produces different results (significant pathways, p values, etc.).
This effect has to do with the permutation number: number of times to shuffle the genes in the gene set.

### Goal: 

Find out a permutation number that gives us reliable results (consistent throughout runs), and runs in a reasonable amount of time.


### Dataset:

Gene expression matrices from mouse liver normal and liver tumor samples.

### Method:

**Repeatability** was used to measure the reliability of runs (10 iterations for each permutation number).

Repeatability = (intersection of the significant pathways of the samples) / (union of the significant pathways of the samples)

**Step 1**: Calculate repeatability for runs with each pre-set permutation number

**Step 2**: Plot a graph showing the relationship between repeatability and permutation number

### Result:

As seen in the figure below, when the permutation number increases, better repeatability is achieved.

In this dataset, it may be suggested that **permutation number = 600** is a good parameter, that gives us reliable results in a reasonable amount of time.

*Red line*: repeatability is calculated using all 10 iterations for each permuation number

*Purple line*: repeatability is calculated using pairwise intersection and union within the 10 iteration; then take average

![Repeatability vs. Permutation number](https://github.com/miko-798/GSEA/blob/master/Practice/repeat.png)




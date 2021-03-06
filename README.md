# nbregression

The nbregression model is a Bayesian generalized linear regression model (GLM), which can be used to perform statistical inference on single-cell RNA-seq data. It was described in Zeisel et al. *Cell types in the mouse cortex and hippocampus revealed by single-cell RNA-seq* **Science** 2015 (PMID: [25700174](http://www.ncbi.nlm.nih.gov/pubmed/25700174), doi: [10.1126/science.aaa1934](http://dx.doi.org/10.1126/science.aaa1934)). Please cite this paper if you use the nbregression algorithm in your work.

The regression model was implemented in [Stan](http://mc-stan.org/) by Sten Linnarsson, with a Python wrapper and command-line tool by Peter Lönnerberg. `nbregression` takes input in CEF format and produces an annotated CEF file as output. Use [ceftools](https://github.com/linnarsson-group/ceftools) to create and manipulate CEF files.

## Input

The input should be a matrix of expression values, in molecules/cell, with genes in rows and cells in columns. Two column attributes must be defined: one that gives the total molecule count per cell, and one that gives the class label for each cell. 

## Output

The result is generated by expanding each row in the input. By default, 1000 samples are generated for each row. Thus, if the input had 20,000 rows, the output will be 20,000,000 rows. A new row attribute `nbr_sample`is added, containing an index of the sample (1, 2, 3, .... 999, 1000). Tip: since the output can be large, it's a good idea to compress it before saving: `nbregression < indata.cef | gzip > outdata.cef.gz`. Compression rates are usually around 10-fold.

...work in progress...

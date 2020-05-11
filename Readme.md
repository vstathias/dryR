# dryR
`dryR` is an R package that provides the statistical framework to assess differential rhythmicity of temporal RNA-Seq datasets of two and more conditions.

## Getting Started

These instructions will get you a `dryR` running on your machine. 

### Prerequisites
You need to install R (see https://www.r-project.org/). 

`dryR` accepts count data typically produced by RNA-Seq with a time dimension and several conditions/groups. The input count data should contain only integer values and be organized in a matrix with rows indicating a specific gene and the column refering to a sample. 

The pipelines to produce these count data from RNA-Seq data (FASTQ files) are described in more details here:
http://master.bioconductor.org/packages/release/workflows/vignettes/rnaseqGene/inst/doc/rnaseqGene.html

A user-friendly web application to generate a count table from FASTQ files is provided here: https://amp.pharm.mssm.edu/biojupies/

### Installing

To install `dryR` run the following code in R.
```
install.packages("devtools")
devtools::install_github("benjaminweger/dryR")
```

## example dataset 
`dryR` comes with example data in form of a list called simData. The list contains count data simData[["countData"]], a vector with the different conditions/groups simData[["group"]], and a vector indicating Zeitgeber Time simData[["time"]]. The data has been generate using simphony https://github.com/hugheylab/simphony.

## Running an example
```
require("dryR")

# prepare arguments
countData = simData[["countData"]]
group     = simData[["group"]]
time      = simData[["time"]]

# run the analysis
dryList   = dryseq(countData,group,time)

# explore the results
dryList[["results"]]    # data frame summarizing results
dryList[["parameters"]] # coefficients: phase, amplitude and mean for each group
dryList[["ncounts"]]    # normalized counts
dryList[["counts"]]     # raw counts
dryList[["cook"]]       # cook's distance for outlier detection
```

## Help
A documentation using `?dryseq` is available. 

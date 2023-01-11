## Importing your fasta fiel of representative sequences of ASV/OTUs
To do this well use the biostrings package (a dependancy of AmphiBac, so its already installed)
```
library(biostrings)
fasta.file<-readDNAStringSet("fasta.file.fna")
```
Thats it. Not everything has to be hard with coding.


## From biom format
Do you have a file with an extension ".biom"? This is the Biological Observation Matrix (BIOM, http://biom-format.org/). This is a fairly common format, in particular if youve used QIIME1 or things associated with the Earth Microbiome Project. 

To use this type of file in R, well need to harness the 'biomformat' in R (https://github.com/joey711/biomformat). Lets start by installing it:

```
#first we need bioconductor as this isn't on CRAN
if (!require("BiocManager", quietly = TRUE))
  install.packages("BiocManager")
BiocManager::install(version = "3.16")

#when prompted enter 'a'

#next install biomformat package
source("http://bioconductor.org/biocLite.R")
biocLite("biomformat")
```

With that installed let import your biom file.

```
library(biomformat)
CODE
```

Now youre allset for AmphiBac analysis like a pro. 

## From Mothur

You work in mothur? Lucky you, you dont need to really do anything. Simply import your ASV/OTU table to R with the code below.
```
asv.tbl<-read.table("your_table.txt", row.names=1, header=T, skip=1)
```

## From phyloseq

## QIIME2 QZA
if (!requireNamespace("devtools", quietly = TRUE)){install.packages("devtools")}
devtools::install_github("jbisanz/qiime2R")

#https://forum.qiime2.org/t/tutorial-integrating-qiime2-and-r-for-data-visualization-and-analysis-using-qiime2r/4121

## DADA2 (R)

## USEARCH/VSEARCH


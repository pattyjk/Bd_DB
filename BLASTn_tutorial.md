## Bd DB BLASTn tutorial

NCBI's BLASTn is of the most commonly used tools for the anlysis of DNA and protein sequce data. From the NCBI website: 

"The Basic Local Alignment Search Tool (BLAST) finds regions of local similarity between sequences. The program compares nucleotide or protein sequences to sequence databases and calculates the statistical significance of matches. BLAST can be used to infer functional and evolutionary relationships between sequences as well as help identify members of gene families."

BLASTn is fast, accurate, and easy to understand for even novice users. This tutorial will guide the user through the use of PACKAGE NAME using NCBI's BLASTn to identify a small amphbian microbiome dataset.

Fell free to plug your own data in here, but let's start by loading data from the package. 

```
#if you haven't installed the package run the first command. If the package is installed, skip to command #2. 
install.packages("PACKAGE NAME")
library(PACKAGE NAME)
data(mock_microbiome)
```

By loading the data we can see we get two key items: (1) sequences and (2) a amlpicon sequence variant (ASV table) from QIIME2. The sequeces here are a subset of a representative set of sequences of the 16S rRNA gene from ORGANISM. The ASV table, as you'll notice is in the format ASVs as row names and column names as samples. If you are loading your data into R you should check out our tutorial on loading data for PACKAGE NAME.

```
str(sequences)


str(ASV_table)
```

## Bd DB BLASTn tutorial

NCBI's BLASTn is of the most commonly used tools for the anlysis of DNA and protein sequce data. From the NCBI website: 

"The Basic Local Alignment Search Tool (BLAST) finds regions of local similarity between sequences. The program compares nucleotide or protein sequences to sequence databases and calculates the statistical significance of matches. BLAST can be used to infer functional and evolutionary relationships between sequences as well as help identify members of gene families."

BLASTn is fast, accurate, and easy to understand for even novice users. This tutorial will guide the user through the use of PACKAGE NAME using NCBI's BLASTn to identify a small amphbian microbiome dataset. This tutorial assumes you haven't set up at BLASTn database.

Fell free to plug your own data in here, but let's start by loading data from the package. 

```
#if you haven't installed the package run the first command. If the package is installed, skip to command #2. 
install.packages("PACKAGE NAME")
library(PACKAGE NAME)
data(mock_microbiome)
```

By loading the data we can see we get three  items: (1) sequences and (2) a amlpicon sequence variant (ASV table) from QIIME2, and (3) metadata for the samples. The sequeces here are a subset of a representative set of sequences of the 16S rRNA gene from ORGANISM in FASTA format (see: https://zhanggroup.org/FASTA/#:~:text=What%20is%20FASTA%20format%3F,by%20lines%20of%20sequence%20data). Could you technically use raw sequence reads here? Yes, but they would need to be converted to FASTA format first and it would take much more time and probably not worth your time. 

The ASV table, as you'll notice is in the format ASVs as row names and column names as samples. If you are loading your data into R you should check out our tutorial on loading data for PACKAGE NAME.

```
str(sequences)


str(ASV_table)
```

Cool, data! Now that we have our data let's set up our BLAST database from the sequences from the DATABASE NAME. 

```
#this first command downloads the latests (and definatley greatest) version of the database and the associated metadata. It writes two R objects and two files (one for DNA sequences, one for metadata). 

COMMAND!!

#this second takes the DNA sequences and creates a NCBI BLAST database. This command relies on the NCBI function 'makeblast_db' (in case you're wondering). 

COMMAND!!!
```

With that out of the way, we're ready to go. Let's run the command to compare our microbiome sequences to our database using BLASTn (aren't you excited?).

```
COMMAND!!!
```

This is just one version of the command and you can modify it as necessary (see documentation). The resulting output of the command is a file written to your computer (in this case named XXX) and a R object (also named). Let's examine this output.

```
str(output)
```

We can see we have columns for the following:

1.  Query                 Your sequences
2.  Database_Match        Match in database
3.  Percent_Identity      percentage of identical matches
4.  Length                alignment length (sequence overlap)
5.  Mismatch              number of mismatches
6.  Gapopen               number of gap openings
7.  Query_Start           start of alignment in query
8.  Query_end             end of alignment in query
9.  Database_start        start of alignment in subject
10.  Database_End         end of alignment in subject
11.  Evalue               expect value
12.  Bitscore             bit score

The key ones here are: 

(1) percent identity

Percent identity is the match of our microbiome to the database. IN this example they're all 100, meaning they're 100% similar. In the command you can flag the "XX option" to change this, but we reccomend, given the small length of most microbiome sequencing reads, to use 100%. 

(2) e-value

This is a statistice from BLASTn about how good a match our sequences are to one another. While not a p-value, it can be interpreted in a similar fashion as a p-value. A common threshold to use as a cutoff for this is e-value <0.05.  To understand more about this see: https://blast.ncbi.nlm.nih.gov/Blast.cgi?CMD=Web&PAGE_TYPE=BlastDocs&DOC_TYPE=FAQ#:~:text=very%20different%20lengths.-,Q%3A%20What%20is%20the%20Expect%20(E)%20value%3F,describes%20the%20random%20background%20noise.. 


(13-X) the metadata for the datbase match

There's a lot here but we have: () the country the microbe orginated from, () the host species of ampbibian was isolated from, () life stage of the amphbian when it was sampled,  () was the amphbiain sampled in the lab or in the wild?, () the latitude and longitude of the sample, () year the microbe was isolated, () method to test inhibition against the fungi, () temperature the assay was conducted at,  () Bd genotype tested, () the 16S sequencing primers used to identify the microbe, () reference, () 16S rRNA gene sequence of the microbe, () taxonomy based on greengenes/per ident, () taxonomy based on SILVA/per ident, () taxonomy based on NCBI/per ident, () genus/species of database microbe

That's a lot of good stuff. Those researchers were quite busy, ey? Now i bet you want to know how much of these bad boys are in your samples, huh? Let's do that next.

```
COMMAND
```

This gives us a brand new ASV table that onyl contains inhibitory ASVs. YOu'll notice that the new table is smaller than the original table (this is normal).

```
dim(old)

dim(new)
```

With this new ASV table you can do any analysis that you want (e.g. alpha diversity, modeling, making pretty pictures). But let's say you want to know the percent of inhibitory taxa in each sample, we an do that too!

```
COMMAND
```
This gives us a data frame with four columns (1) The sample name, (2) the total read count from the original ASV table, (3) the read count for inhibitory ASVs, (4) the percentage of reads that is inhhibitory (column 3/column 4*100).

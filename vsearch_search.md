```
######################vsearch##########################
#needs vsearch exe.
#VSEARCH identification
system2("./vsearch_win/vsearch-2.22.1-win-x86_64/bin/vsearch.exe", args=c("-usearch_global ./test_data/dna-sequences.fasta --db ./BD_DB.fna --strand plus --blast6out test_closed.txt --id 1"))

#read in table to R
vsearch_results<-read.delim("./test_closed.txt", header=F, col.names = c('Query', 'Database_Match', "Percent_Identity", "Length", "Mismatch", "Gapopen", "Query_Start", "Query_End", "Database_Start", "Database_End", 'Evalue', "bitscore"))
```

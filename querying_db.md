```
#make blast database, neeed blast exe
#makes BLAST database in PWD
system2("/Program Files/NCBI/blast-BLAST_VERSION+/bin/makeblastdb", args=c("-in BD_DB.fna -parse_seqids -title BD_DB -out BD_DB -dbtype nucl"))

#query sequences against BLAST DB just created
system2("/Program Files/NCBI/blast-BLAST_VERSION+/bin/blastn", args=c("-query ./test.txt -db ./BD_DB -out results.txt -outfmt 6 -max_hsps 1 -max_target_seqs 1"))

#read file in and add headers
blast_results<-read.delim("results.txt", header=F, col.names = c('Query', 'Database_Match', "Percent_Identity", "Length", "Mismatch", "Gapopen", "Query_Start", "Query_End", "Database_Start", "Database_End", 'Evalue', "bitscore"))

##What each output is directly from BLASTn
#1.  qseqid      query or source (e.g., gene) sequence id
#2.  sseqid      subject  or target (e.g., reference genome) sequence id
#3.  pident      percentage of identical matches
#4.  length      alignment length (sequence overlap)
#5.  mismatch    number of mismatches
#6.  gapopen     number of gap openings
#7.  qstart      start of alignment in query
#8.  qend        end of alignment in query
#9.  sstart      start of alignment in subject
#10.  send        end of alignment in subject
#11.  evalue      expect value
#12.  bitscore    bit score

#needs UCLUST exe.
#UCLUST identification
system2("./usearch11.0.667_win32.exe", args=c("-closed_ref ./test.txt -otutabout test2.txt -db ./BD_DB.fna -strand plus -tabbedout closed.txt"))

#read in table to R
uclused_results<-read.delim("./closed.txt", header=F, col.names=c('Query', "X", "Y", "Database_Match", "Percent_Identity", "Z"))[,-c(2,3,6)] 
```

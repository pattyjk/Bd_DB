```

bd_meta$Country
bd_meta$Wild.Captive
bd_meta$Host.Species
bd_meta$Life.Stage


##############################BLAST
#blast exes have to be downloaded and installed
#https://ftp.ncbi.nih.gov/blast/executables/blast+/LATEST/
#windows- downloard the .exe file and simply double click to install. Nothing more needed. It will be callable in R
#Linux- in terminal simply run sudo apt install ncbi-blast+, to test in terminal try blastn -h. Now its callable in R
#MacOS- navigate to https://ftp.ncbi.nlm.nih.gov/blast/executables/blast+/LATEST/ and downloard the MacOS exe. In the Mac Terminal navigate to where the file was downloaded
#run tar -xvf file
#can move elsewhere, but fine to keep where is
#next run nano ~/.profile and then paste
#export PATH=[loc to bin folder]:${PATH}
#[loc to bin folder is the bin folder we extracted in a previous step]
#press control o and control x
#if this works (it should), close the terminal and open a new terminal and type 'blastn -h' and you should have a working blast

#make blast database, neeed blast exe installed
#makes BLAST database in PWD
system2("makeblastdb", args=c("-in BD_DB.fna -parse_seqids -title BD_DB -out BD_DB -dbtype nucl"))

#query sequences against BLAST DB just created
system2("blastn", args=c("-query ./test_data/dna-sequences.fasta -db ./BD_DB -out results.txt -outfmt 6 -max_hsps 1 -max_target_seqs 1"))

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




blast_search<-function(input, database, output){
  
  system2("./usearch11.0.667_win32.exe", args=c("-closed_ref input -db database -strand plus -tabbedout output"))
  
}
```

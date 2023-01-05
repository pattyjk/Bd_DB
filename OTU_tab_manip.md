## Manipulating OTU table and calculating percent inhibitory

# Need to add for enhancing/no effect
```
#read OTU table
otu.tab<-read.table("test_data/julia_asv_table.txt", header=T, row.names=1)

#filter OTU table by inhibitory OTUs
otu.tab.inhib<-na.omit(otu.tab[vsearch_results$Query,])

#create column sums for each sample for the original OTU table
otu.tab.sum<-as.data.frame(colSums(otu.tab))
names(otu.tab.sum)<-"Total_Reads"

#create column sums for the inhibitory table
otu.tab.sum2<-as.data.frame(colSums(otu.tab.inhib))
names(otu.tab.sum2)<-"Inhibitory_Reads"

#calculate percent inhibitory for each sample
per_inhib<-cbind(otu.tab.sum, otu.tab.sum2)
per_inhib$percent_inhibitory<-per_inhib$Inhibitory_Reads/per_inhib$Total_Reads
per_inhib$SampleID<-row.names(per_inhib)
```

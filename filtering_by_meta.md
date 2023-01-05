```
#Filtering database based on metadata

bd_meta<-read.delim("./Bd_DB_meta.txt", header=T)

country_mada<-bd_meta[which(bd_meta$Country =='Madagascar' | bd_meta$Country == 'Colorado'),]
country_mada<-bd_meta[which(bd_meta$Country =='Madagascar'),]  
  
#load biostrings
library(Biostrings)

#read in fasta with biostrings
bd_fasta<-readDNAStringSet("BD_DB.fna")

#easy subset by the files
testy<-bd_fasta[country_mada$Isolate.name]

#categories of interest
bd_meta$Country
bd_meta$Wild.Captive
bd_meta$Host.Species
bd_meta$Life.Stage
```

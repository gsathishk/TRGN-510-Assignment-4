##### TRGN 510 Assignment 4 Task 3.
##### Sathish Kumar Ganesan.
##### 18 Feb 2018.
###### We load in libraries.
`
library(ggplot2) 
library(plotly)
`
###### We Change Directory.
`
setwd('~/testgraph2/mygraph2/bin/')
`
#We load in our dataframe.
skgkgenes <- read.csv('gene_dist_head.tsv', header= TRUE, sep = "\t",fill = TRUE) 
#We define a factor set of autosomes.
autosomes<-c("1","2","3","4","5","6","7","8","9","10",
             "11","12","13","14","15","16","17","18","19","20","21","22")  
#We create a new dataframe called 'genes' which only has autosomes, however we still have those additional factors.
genes<- skgkgenes[ which(skgkgenes$chr %in% autosomes), ] 
#We remove the factors and then order them so they are numerical order and not alphabetical.
genes$chr <- factor(genes$chr, levels = autosomes) 
#We plot in ggplot. 
ggplot(data = genes) +  geom_bar(mapping = aes(x = chr, fill = feature), width = 1)
ggplot(data = genes) + geom_bar(mapping = aes(x = feature))
ggplot(data = genes) + geom_bar(mapping = aes(x = chr, fill = feature))
ggplot(data = genes) + geom_bar(mapping = aes(x = chr, fill = feature), width = 1) + coord_polar()
#Here we install devtools to make ggplotly work.
install.packages('devtools')
devtools::install_github('hadley/ggplot2')
p <- ggplot(data = genes) + geom_bar(mapping = aes(x = chr, fill = feature), width = 1)
ggplotly(p)
#This should generate a plot with tooltips.

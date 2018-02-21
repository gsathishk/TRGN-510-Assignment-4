```{r}
setwd('~/testgraph2/mygraph2/bin/')
library("ggplot2")
library("plotly")
skgkgenes <- read.csv('gene_dist_head.tsv', header= TRUE, sep = "\t",fill = TRUE)
autosomes <-c ("1","2","3","4","5","6","7","8","9","10","11","12","13","14","15","16","17","18","19","20","21","22")
genes <- skgkgenes[ which(skgkgenes$chr %in% autosomes), ]
genes$chr <- factor(genes$chr, levels = autosomes)
ggplot(data = genes) +  geom_bar(mapping = aes(x = chr, fill = feature), width = 1)
ggplot(data = genes) + geom_bar(mapping = aes(x = feature))
ggplot(data = genes) + geom_bar(mapping = aes(x = chr, fill = feature))
ggplot(data = genes) + geom_bar(mapping = aes(x = chr, fill = feature), width = 1) + coord_polar()
install.packages("devtools", repos = "http://cran.us.r-project.org")
devtools::install_github('hadley/ggplot2')
p <- ggplot(data = genes) + geom_bar(mapping = aes(x = chr, fill = feature), width = 1)
ggplotly(p)
summary(skgkgenes)
```

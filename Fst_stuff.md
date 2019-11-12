# vcftools
```
./vcftools --vcf input_data.vcf --weir-fst-pop population_1.txt --weir-fst-pop population_2.txt --out pop1_vs_pop2
```

# Ploting with R

```R
# Making an Fst plot using ouput from vcftools

# Working directory
setwd("~/Documents/PhD/woodshole2019/borealis")

# Loading necessary libraries
library(dplyr)
library(tidyr)
library(ggplot2)

borealis_Fst <- read.table("east_M_VS_F_sliding.txt.windowed.weir.fst",sep="\t", header=TRUE) 
#str(borealis_Fst)

#create a new column for color depending on non recombining (red) region or not (black)
borealis_Fst <- borealis_Fst %>%
  mutate(
    color_plot = case_when(
      BIN_START <= 57000000 ~ "red", #NEED to use the real coordinates, used Furman on laevis
      TRUE ~ "black"
    )
  )%>%
  arrange(BIN_START) #re-ordering
    
plot_fst <- ggplot(borealis_Fst) +
  geom_point(aes(BIN_START,MEAN_FST,
             colour=color_plot))+
  scale_colour_identity()

#Changing labels and get rid of background color
plot_fst + 
  labs(title="Fst - Chr.08L",
       y ="Fst mean", x = "Bin start")+
  theme_bw() + 
  theme(panel.grid.major = element_blank(), panel.grid.minor = element_blank(),
        panel.border = element_blank())

```

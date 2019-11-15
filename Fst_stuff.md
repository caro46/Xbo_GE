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
# Finding the non-recombining region in *X. borealis* genome

From Furman paper, against *X. laevis* genome (v. 9.1): `chr8L: 4,605,306..51,708,524`:

- `Xelaev18038326m.g`: `chr8L:4,601,429..4,602,090`

- `ppp1r26.L`: `chr8L:4,528,671..4,545,909`

- `egfl8.L`: `chr8L:51704666..51725357`


```
module load blast/2.2.28+
blastn -evalue 1e-20 -query Xborealis_SD_region.fa -db /work/ben/2018_Austin_XB_genome/Xbo.v1.fa_blastable -out Xborealis_SD_region_Xbo_v1_e20out6.out -outfmt 6

#egfl8.L_chr8L   Chr8L   85.54   892     105     18      18785   19665   61525518        61524640        0.0      911
#ppp1r26.L_chr8L Chr8L   88.29   2724    284     22      1974    4664    2069408 2072129 0.0     3230
#ppp1r26.L_chr8L Chr8L   88.65   1119    76      24      4704    5815    2072130 2073204 0.0     1315

```
`Xelaev18038326m.g` found on `Chr6S` and `Chr1S`.

Maybe better coordinates to use: `chr8L:2069408..61524640`.

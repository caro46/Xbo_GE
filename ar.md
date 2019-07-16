# Getting flanking region of exons

## Why?

Exons from the transcriptome of *X. borealis* are too small (especially the targetted exon2) to design primers.
Need the flanking region of the target from *X. borealis* assembly.

## Getting location of exon

Blasting the exon of interest onto the *X. borealis* reference genome to get the coordinates (doing for **BOTH** isoforms). 

```
module load blast/2.2.28+
blastn -evalue 1e-20 -query ar_partial_transcript_exon2.fa -db /work/ben/2018_Austin_XB_genome/Xbo.v1.fa_blastable -out Xbo_ar_transcript_exon2partial_Xbo_v1_out6.out -outfmt 6

```
Now we have the location of the exon in the genome. Let's extract flanking region to simplify the design of primers.

## Extracting sequences of interest

### Bbmap

I already have Bbmap installed on Sharcnet and their scripts are always good and super useful. Could have used Bedtools but I don't have it installed.

```
../programs/bbmap/filterbyname.sh in=/work/ben/2018_Austin_XB_genome/Xbo.v1.fa out=Xbo.v1.ar_exon2.L.fa names=Chr8L include=t substring from=18156000 to=18156500

../programs/bbmap/filterbyname.sh in=/work/ben/2018_Austin_XB_genome/Xbo.v1.fa out=Xbo.v1.ar_exon2.S.fa names=Chr8S include=t substring from=17416400 to=17416800
```
### Other programs

```bash
cat test.bed
#chr1 5 10

# optionally write to an output file
bedtools getfasta -fi test.fa -bed test.bed -fo test.fa.out
```
## Designing primers

Using Primer3 in Geneious: select the target region then > Design new primers > Forward & Reverse > Target region > Number of pairs to generate (set to at least 5 then pick the best). 

Using primer-blast on NCBI you can (somewhat) check specificity of the primers (keep in mind that you might have a diverse species from the available data and if you you refseq but you have intron then I might not really be representative). It gives an idea of how good and specific the primers couple is. You can also blast on Xenbase and see if there is only 1 hit for each primer.

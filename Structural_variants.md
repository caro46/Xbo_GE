# Goal

We have access to a good *X. borealis* female assembly. BJE has also HiSeqX reads of both a female and a male. The idea is to try to use the reads information (orientation, splitting) to identify structural variant on the W chromosome (specific to the female). The most interesting to first check is inversion.

Some interestin info [here](https://deepseqanalysis.readthedocs.io/en/latest/re-seq-align-struct.html).

# Lumpy ([article](https://genomebiology.biomedcentral.com/articles/10.1186/gb-2014-15-6-r84), [github](https://github.com/arq5x/lumpy-sv#lumpy))

## Note about installation
A mistake in the installation instruction. Need to use:
```
git clone  --recursive  https://github.com/arq5x/lumpy-sv
```
Load the good python version on graham before `make` (`module load python/2.7`) to have access to the good libraries (especially `pysam`, need to do `module load mefit/1.0`).

## VCF output description

```
##fileformat=VCFv4.2
##source=LUMPY
##INFO=<ID=SVTYPE,Number=1,Type=String,Description="Type of structural variant">
##INFO=<ID=SVLEN,Number=.,Type=Integer,Description="Difference in length between REF and ALT alleles">
##INFO=<ID=END,Number=1,Type=Integer,Description="End position of the variant described in this record">
##INFO=<ID=STRANDS,Number=.,Type=String,Description="Strand orientation of the adjacency in BEDPE format (DEL:+-, DUP:-+, INV:++/--)">
##INFO=<ID=IMPRECISE,Number=0,Type=Flag,Description="Imprecise structural variation">
##INFO=<ID=CIPOS,Number=2,Type=Integer,Description="Confidence interval around POS for imprecise variants">
##INFO=<ID=CIEND,Number=2,Type=Integer,Description="Confidence interval around END for imprecise variants">
##INFO=<ID=CIPOS95,Number=2,Type=Integer,Description="Confidence interval (95%) around POS for imprecise variants">
##INFO=<ID=CIEND95,Number=2,Type=Integer,Description="Confidence interval (95%) around END for imprecise variants">
##INFO=<ID=MATEID,Number=.,Type=String,Description="ID of mate breakends">
##INFO=<ID=EVENT,Number=1,Type=String,Description="ID of event associated to breakend">
##INFO=<ID=SECONDARY,Number=0,Type=Flag,Description="Secondary breakend in a multi-line variants">
##INFO=<ID=SU,Number=.,Type=Integer,Description="Number of pieces of evidence supporting the variant across all samples">
##INFO=<ID=PE,Number=.,Type=Integer,Description="Number of paired-end reads supporting the variant across all samples">
##INFO=<ID=SR,Number=.,Type=Integer,Description="Number of split reads supporting the variant across all samples">
##INFO=<ID=BD,Number=.,Type=Integer,Description="Amount of BED evidence supporting the variant across all samples">
##INFO=<ID=EV,Number=.,Type=String,Description="Type of LUMPY evidence contributing to the variant call">
##INFO=<ID=PRPOS,Number=.,Type=String,Description="LUMPY probability curve of the POS breakend">
##INFO=<ID=PREND,Number=.,Type=String,Description="LUMPY probability curve of the END breakend">
##ALT=<ID=DEL,Description="Deletion">
##ALT=<ID=DUP,Description="Duplication">
##ALT=<ID=INV,Description="Inversion">
##ALT=<ID=DUP:TANDEM,Description="Tandem duplication">
##ALT=<ID=INS,Description="Insertion of novel sequence">
##ALT=<ID=CNV,Description="Copy number variable region">
##FORMAT=<ID=GT,Number=1,Type=String,Description="Genotype">
##FORMAT=<ID=SU,Number=1,Type=Integer,Description="Number of pieces of evidence supporting the variant">
##FORMAT=<ID=PE,Number=1,Type=Integer,Description="Number of paired-end reads supporting the variant">
##FORMAT=<ID=SR,Number=1,Type=Integer,Description="Number of split reads supporting the variant">
##FORMAT=<ID=BD,Number=1,Type=Integer,Description="Amount of BED evidence supporting the variant">
```
## Checking results
```
zgrep "<INV>" Chr8L_dad.vcf.gz | zless
zgrep "<INV>" Chr8L_mom.vcf.gz | awk '{split($8,aa,";");print $1,$2,aa[3],aa[4]}'
zgrep "<INV>" Chr8L_mom.vcf.gz | zgrep -v "IMPRECISE" |zless

module load nixpkgs/16.09  gcc/5.4.0 samtools/1.9
samtools tview -p Chr8L:566666 DAD_to_AustinXB_sorted.bam Xbo.v1.fa
`````
Can also open the bam files (afer indexing and only the region of interest) locally with `IGV_2.3.81`. The reference assembly also need to be indexed.

```
samtools faidx <ref.fa>
samtools index MOM_to_AustinXB_8L_INV_sorted.bam
```

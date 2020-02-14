# Extracting the *X. borealis* paralogs

Blasted sox3 amplicons Martin got from new primers onto *X. borealis* genome. Extract the paralogs using bbmap

```
module load blast/2.2.28+
blastn -evalue 1e-20 -query Xbo_sox3_potential_8L_for_Martin.fasta -db /work/ben/2018_Austin_XB_genome/Xbo.v1.fa_blastable -out Xbo_sox3_amplicons_Martin_jan16_2020_location_Xbo_v1_out0.out -outfmt 0

../programs/bbmap/filterbyname.sh in=/work/ben/2018_Austin_XB_genome/Xbo.v1.fa out=Xbo.v1.sox3_partial.L.fa names=Chr8L include=t substring from=37849020 to=37850506
../programs/bbmap/filterbyname.sh in=/work/ben/2018_Austin_XB_genome/Xbo.v1.fa out=Xbo.v1.sox3_partial.S.fa names=Chr8S include=t substring from=34489700 to=34491042
cat Xbo.v1.sox3_partial.L.fa Xbo.v1.sox3_partial.S.fa >Xbo.v1.sox3_partial.both_paralogs.fa
```
Same for sf1
```
module load blast/2.2.28+
blastn -evalue 1e-20 -query Xbo_clone_martin_sf1.fa -db /work/ben/2018_Austin_XB_genome/Xbo.v1.fa_blastable -out Xbo_clone_martin_sf1_XboV1.0_Austin_out6.out -outfmt 6
../programs/bbmap/filterbyname.sh in=/work/ben/2018_Austin_XB_genome/Xbo.v1.fa out=Xbo.v1.sf1_partial_martin.L.fa names=Chr8L include=t substring from=12083800 to=12084500
./programs/bbmap/filterbyname.sh in=/work/ben/2018_Austin_XB_genome/Xbo.v1.fa out=Xbo.v1.sf1_partial_martin.S.fa names=Chr8S include=t substring from=12857000 to=12857700
cat Xbo.v1.sf1_partial_martin.L.fa Xbo.v1.sf1_partial_martin.S.fa >Xbo.v1.sf1_both_partial_paralogs_martin.fa
```

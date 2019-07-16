Need the flanking region of the target from *X. borealis* assembly.

```bash
cat test.bed
#chr1 5 10

# optionally write to an output file
bedtools getfasta -fi test.fa -bed test.bed -fo test.fa.out
```

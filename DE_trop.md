# Sex specific - gene level

## Male specfic (Y)

- `Xetrov90003943m` , `Chr02:4313545-4314296` (v.9.1)

## Female biased

- `LOC100497740`, Chr.07 (`Chr07:108008304-108025591` (v.9.1)): mlc2 (`AC160829.3`) = myosin light chain 2

### Looking into scaffolds:
- `a2ml1`: scaffolds in *X. tropicalis* (`scaffold_244:7555-53183` (v.9.1)) and *X. laevis*), **trop v.10.7: `Chr7:6718182..6776149`** --- very small exons
- `LOC100145515` (`LOC100145515	scaffold_281:89239-109531` v9.1): Predicted E3 ubiquitin ligase (after blasting against mRNA database on xenbase) - See [Ehrlund et al. 2009](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC2663311/) and from [Uniprot page of fem-1](https://www.uniprot.org/uniprot/P17221):

*Sex-determining protein; essential for the adoption of the male sexual fate in all tissues. Substrate recognition subunit of the cullin-RING-based CBC(fem-1) (Cul2-ElonginB-ElonginC) E3 ubiquitin-protein ligase complex which mediates in association with cofactors fem-2 and fem-3 the ubiquitination and subsequent proteasomal degradation of tra-1.*

Blasted (blastx) exon of 489bp (`scaffold_281 scaffold_281:98337..98825`) on NCBI to identify potential domain:
```
RING-HC_TRIM47_C-IV 	cd16604 	
RING finger, HC subclass, found in tripartite motif-containing protein 47 (TRIM47)
	2-49 	3.86e-0
  
RING finger, HC subclass, found in tripartite motif-containing protein 47 (TRIM47) and similar proteins
TRIM47, also known as gene overexpressed in astrocytoma protein (GOA) or RING finger protein 100 (RNF100), belongs a subclass of TRIM (tripartite motif) family of proteins that are defined by their N-terminal RBCC (RING, Bbox, and coiled coil) domains, including three consecutive zinc-binding domains, a C3HC4-type RING-HC finger, a B-box, and two coiled coil domains, as well as a B30.2/SPRY (SplA and ryanodine receptor) domain positioned C-terminal to the RBCC domain. It plays an important role in the process of dedifferentiation that is associated with astrocytoma tumorigenesis.
```
For protein see genbank `AAI61185.1`. 

It seems to be a specific copy of *X. tropicalis*. A copy of the gene is on chromosome 8 in *X. tropicalis* and 8L/S in *X.laevis*. Exact match for `Chr8:143803609..143825810` in *X. tropicalis* v.10.7

Designed primers with primer-blast (Primer3 on NCBI) using the ref. `XM_018090095.1` and specificity to *X.tropicalis*. Designed primers for 2 big exons: exons 4 and 6.

- `ambp`: Chr.08L in *X.laevis*, *X. tropicalis* v.10.7: `Chr8:2834392..2835173`

## Male biased

- `gene369` (`LOC100491523: scaffold_130:375544-390925`) = ph1 (`XR_001923395.1`) = polyhomeotic-like protein 1, scaffold 130 (v.9.1). On *X. tropicalis* v.10.7: `Chr7:7775079..7791196` 

[Uniprot](https://www.uniprot.org/uniprot/Q64028):
```
Tissue specificity:
Highly expressed in testis with lower levels in most other tissues. Expressed in embryonic stem cells
```

# Sex specific - transcript level

## Male specific

```
#TRINITY_DN5848_c0_g1_i2 (scaffold_132 v9.1) = vwa2: Chr7:3970247..3989763
#TRINITY_DN2504_c0_g2_i3 scaffold_108 456770..459556: Chr7:7635900-7638685
#TRINITY_DN1080_c0_g1_i4 scaffold_130: 758463..770091 = phc1 Chr7:7982516..7994580
```
### phc1

- Amplified using primers from Bewick et al. 2013 (scaf2_150071042_f: `GATTGGTCCCCTTCCGTAAT` / scaf2_150071793_r: `GGATTTCAGGCCAGCAGTTA`)

- `TRINITY_DN1080_c0_g1_i4`: male specific, `TRINITY_DN1080_c0_g1_i1`: expressed in everybody.


### vwa2

- Downloaded the *X.tropicalis* reference mRNA of the gene from xenbase version 10.0 (Name: `XM_004919370.2`, Position: `Chr7:3970247..3989763 (+ strand)`, ID: `rna36218`, Transcript_id: `XM_004919370.2`, Original_region: `scaffold_132:209568-228197`). 

- MAFFT (https://mafft.cbrc.jp/alignment/software/) with default parameters to align the annotated mRNA and both transcripts (`TRINITY_DN5848_c0_g1_i2` male specific, `TRINITY_DN5848_c0_g1_i1` expressed in everybody). The differences between both of our transcripts are within the 3' UTR region.

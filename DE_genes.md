# Rational

Most "interesting" genes to potentially target would be:

- female specific = on the W chromosome
- male biased = on the Z chromosome (assuming no dosage compensation)

and located on the chr.8L in the non recombining region identified previously by BenF.

# Sex specific genes

## Female specific

### Xenbase mRNA database (*X. tropicalis* + *X. laevis*) - Blast 

- `TRINITY_DN12136_c1_g1_i1` = zbtb43.S = zinc finger and BTB domain containing 43

- `TRINITY_DN25319_c0_g1_i3` = ammecr1.L = Alport syndrome, mental retardation, midface hypoplasia and elliptocytosis chromosomal region gene 1
 - after having to blast the hit sequence from `Xelaev18038801m` back to the *X. laevis* genome

Both genes are in the reduced region of non-recombination identified by BenE.

### Located on *X. laevis* scaffold

- odf2 = outer dense fiber of sperm tails 2 - located on *X. tropicalis* chromosome 8. A bit weird and surprising that this gene seem female sepcific while in other species it is the opposite.

Used FDR <0.05 regardless on the location. odf2 is only expressed in females and for both stages (reads count 247 - 610). odf2 is located on 8 in *X. tropicalis* (scaffold in *X. laevis*). In *X. laevis* it is only expressed in testis. ODF genes seem to have a very conserved role in spermatogenesis even in mammals... 

Need to check if within the shorter region identified by BenE. --- It is!

## Male specific

- `LOC108699136` on xenbase (Xlaev.9.2). Use the gene sequence from xenbase to blastn on NCBI: Xnr5 (`AB219931.1`) = tandem repeat of Xenopus nodal-related 5

- `LOC108699425` on xenbase (Xlaev.9.2). NCBI: `XM_018253512.1` = Xenopus laevis pulmonary surfactant-associated protein C-like (LOC108711616), mRNA

# Sex biased

## Male biased

- `LOC108698289` = Naa10 (when xenbase sequence blasted to NCBI) = N(alpha)-acetyltransferase 10, NatA catalytic subunit. NAA10/NAA11 seem involved in spermatogenesis with NAA10 being on X-chromosome, potentially inactivated in males (see [Lee et al. 2018](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6063908/))

- `LOC733244` = Xenopus laevis type I activation TM-receptor XFL2 L (when xenbase sequence blasted to NCBI

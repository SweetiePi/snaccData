# snacc: Sequence Non-Alignment Compression & Comparison for Inferring Microbial Phylogenies

This repository contains the supplementary data for our manuscript, "Sequence Non-Alignment Compression & Comparison for Inferring Microbial Phylogenies."

Datasets
-----------

* [Carsonella ruddii](http://www.ncbi.nlm.nih.gov/nuccore/CP019943)
* [Listeria monocytogenes](https://figshare.com/articles/_/5483461)
* [Escherichia coli](http://guanine.evolbio.mpg.de/andi/st131_extra.tgz)
* [Streptococcus pneumonaie](https://datadryad.org//resource/doi:10.5061/dryad.t55gq)

Simulations
------------

Simulations of Carsonella rudddii were created using the script mutation.py. Mutation rates used were 0.01, 0.025, 0.05, 0.1, 0.15, and 0.2. 

```
python mutation.py carsonella_reference.fa 0.01 > carsonella_simulated.fa
```

Sequences were reverse complimented by running the script reverse.py

```
python reverse.py carsonella_simulated.fa > carsonella_simulated_reverse.fa
```

Distance matrix construction
------------

Software and versions are described in the paper. Command lines used:

snacc:
```
snacc sequence_directory/ -n 5 -o output.csv
```

andi:
```
andi -j -t 1 sequence_directory/*.fa > output.tsv
```

Mash:
```
mash sketch -o reference.msh sequence_directory/*.fa
mash dist -t reference.msh reference.msh > output.tsv
```

PopPUNK:
For L. monocytogenes:
```
ls sequence_directory/*.fa > reference_list.txt
poppunk --r-files reference_list.txt --min-k 13 --max-k 29 --full-db
```

For E. coli ST131:
```
ls sequence_directory/*.fa > reference_list.txt
poppunk --r-files reference_list.txt --min-k 15 --max-k 29 --full-db
```

For S. pneumoniae:
```
ls sequence_directory/*.fa > reference_list.txt
poppunk --r-files reference_list.txt --min-k 11 --max-k 29 --full-db
```

NCD with PPMZ:
```
ls sequence_directory/*.fa > assemblies.txt
./ncd_distance.pl assemblies.txt > output.txt
```

FastTree:
```
FastTree -nt -gttr < ref_bwa_aln > output.tree
```

RAxML:
```
raxmlHPC-PTHREADS-SSE3 -T 4 -f d -s input.phy -m GTRGAMMA -p 12345 -n output
```





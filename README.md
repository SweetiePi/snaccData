# snacc: An Accurate Alignment-free Method for Inferring Microbial Phylogenies

This repository contains the supplementary data for our manuscript, "snacc: An Accurate Alignment-free Method for Inferring Microbial Phylogenies"

Datasets
-----------

* [Simulated HGT](http://afproject.org/media/genome/hgt/simulated/sim_hgt/dataset/simulated-sim_hgt.zip)
* [Simulated Streptococcus](https://figshare.com/articles/_/5483461)
* [Ecoli/Shigella](http://afproject.org/media/genome/hgt/unsimulated/ecoli_shigella/dataset/unsimulated-ecoli_shigella.zip)
* [Yersinia](http://afproject.org/media/genome/hgt/unsimulated/yersinia/dataset/unsimulated-yersinia.zip)

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

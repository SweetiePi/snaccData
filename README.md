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

Software and versions are described in the manuscript. Command lines used:

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

FFP:
```
./ffpry sequence_directory/*.fa | ./ffpcol | ./ffprwn | ./ffpjsd > output.csv
```

skmer:
```
skmer reference sequence_directory/*.fa -p 4 -k <k-mer size optimized> -o library
skmer distance library -t -o output.csv
```

Co-phylog:
```
./fasta2co directory/sequence.fa | ./co2dist > output.csv
```

OrthoANIu:
```
java -jar OAU.jar -fd sequence_directory/ -u ./usearch_directory -o ./output.csv
```

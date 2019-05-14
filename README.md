Chinese-brain-project eQTL pipeline
====

This repository contains analysis pipelines for:<br>
  * RNA-seq alignment, quantification, and quality control<br>
  * eQTL mapping and functional annotation<br>
  * Intergrate with GWAS summary result<br>
  * Preservation test and robust WGCNA<br>


### Install
```Linux
git clone https://github.com/liusihan/Chinese-brain-project
```

### Softwares
  * R-3.3.3
  * [QTLtools](https://qtltools.github.io/qtltools/)
  * [LDSC](https://github.com/bulik/ldsc)
  * [TWAS](http://gusevlab.org/projects/fusion/#jointconditional-tests-and-plots)



## Usage

### QTl replicatin rate
```R
Rscript pi1.r P.txt
```

`NOTE`: P.txt is a text file with nominal P value per line without header. We recommend use best eQTL in each gene identified in one population or tissue, and then estimates the proportion of these (π1) that detected the same pair in a second population or study to their nominal p-values.


### Robust eQTL
```Linux
bash robust_eQTL.sh sample_size index.txt PEER_factor FDR output_dir raw_counts.txt
```
* sample_size: the sample size you want to perform eQTL analysis
* index.txt: output file for sample index
* PEER_factor: number of peer hidden factor to collect
* FDR: storey FDR qvalue for adjust P value
* output_dir: prefix of output directory
* raw_counts.txt: raw counts data, each column stand for a sample, each raw stand for a gene

`NOTE`: the output_file include three type eQTL results under different mode in QTLtools(nominal/permutation/conditional)

### Create TWAS expressing weights
```Linux
bash TWAS_compute_weights.bash expression GENO covariant.txt
```
* expression: gene expression file with three aditional column: chr, star, end
* GENO: plink bfile for chromosome
* covariant.txt: text file contain the covariants
  
### Robust WGCNA
```R
Rscript ....
```

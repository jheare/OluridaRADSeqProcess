# Methods #
-----
### Sample Processing ###
Thirty-two samples from each population (n=96) from outplant were selected for processing. The samples were isolated using Qiagen 96 well plate kit, digested using the sbfI restriction enzyme, and processed into libraries using a RAD library kit. Samples were then sent off to University of Oregon's Core Processing facility for sequencing. Raw sequence information was sent back to University of Washington in December 2014. 

##
### Processing radtags ###
Raw sequence data was returned in 14 gzipped fastq files. Copies of these files were placed on a read only directory for long term storage. Working versions were unzipped using gzip and then copied into a working directory. A tab delimited barcode file was also created to combine barcodes with the appropriate sample name. This barcode file and fastq files were then processed with STACKS using a sub function called *process_radtags* which demultiplexed the data while removing reads with ambiguous barcodes and radtags. This program then output fastq files containing all the reads for each sample based on the barcode. While no errors are produced from this run, it only produces fastq files with barcodes instead of sample names.

**You can see a notebook of the *process_radtags* workflow [here](https://github.com/jheare/Fish546-Jake/blob/master/Course%20Project/Workflow/Process%20Radtags.ipynb).**
##
### Stacks processing ###
Fastq files produced from *process_radtags* were checked for quality. The top 10 samples containing more than 180k reads were then selected to run through each step of the STACKS process. 

|  Samples Used 	|
|:-------------:	|
| sample_CACCTC 	|
| sample_CCCTAA 	|
| sample_GCTCAA 	|
| sample_GTGTAA 	|
| sample_ACATAC 	|
| sample_ACCATG 	|
| sample_ACCCCC 	|
| sample_CAAAAA 	|
| sample_TACACA 	|
| sample_CAGGCA 	|

#### *ustacks* ####
First the samples were run through the *ustacks* function which assembled the loci for each sample producing a sample.tags.tsv file, then called for SNPs producing a sample.snps.tsv file, and finally determined haplotypes and alleles creating a sample.alleles.tsv. No errors were produced for *ustacks* as it needs no input file to discern populations. 
#### *cstacks* ####
A population map tab delimited file produced outside of STACKS created with sample name and population designation. This file was then applied with the files produced from *ustacks* to *cstacks* to produce catalogs of all loci, snps, and haplotypes for each designated population in files Population.catalog.tags.tsv, Population.catalog.snps.tsv, Population.catalog.alleles.tsv. *cstacks* produced no error in this run but due to the lack of a population file it grouped all the selected samples into a single population catalog. Due to this, analysis during *sstacks* assumes no differences between samples and does not create catalogs around each population. Moving forward this only allows for *sstacks* and *populations* to treat all samples as sourced from a single population. 
#### *sstacks* ####
Finally these catalogs were then used to compare individual samples to the population catalogs using the *sstacks* function which produced a matches file sample.matches.tsv. *sstacks* produces matches.tsv files for each sample only compared to the single population file.


**You can see a notebook of the Stacks process work [here](https://github.com/jheare/Fish546-Jake/blob/master/Course%20Project/Workflow/Stacks%20Process.ipynb).**
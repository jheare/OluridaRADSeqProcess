# Data Record #
##Change to narrative. Describe columns in TSV files as they pertain to the data.##
----
### Raw Sequence Data ###
Raw sequence data was returned in 14 gzipped fastq files. Copies of these files were placed on OWL for long term storage. Working versions were unzipped using gzip and then copied into a **./lane1rad**.

**directory** ./lane1rad

**Work Files**

|            Data Files           	|
|:-------------------------------:	|
| lane1_NoIndex_L001_R1_001.fastq 	|
| lane1_NoIndex_L001_R1_002.fastq 	|
| lane1_NoIndex_L001_R1_003.fastq 	|
| lane1_NoIndex_L001_R1_004.fastq 	|
| lane1_NoIndex_L001_R1_005.fastq 	|
| lane1_NoIndex_L001_R1_006.fastq 	|
| lane1_NoIndex_L001_R1_007.fastq 	|
| lane1_NoIndex_L001_R1_008.fastq 	|
| lane1_NoIndex_L001_R1_009.fastq 	|
| lane1_NoIndex_L001_R1_010.fastq 	|
| lane1_NoIndex_L001_R1_011.fastq 	|
| lane1_NoIndex_L001_R1_012.fastq 	|
| lane1_NoIndex_L001_R1_013.fastq 	|
| lane1_NoIndex_L001_R1_014.fastq 	|

A tab delimited barcode file was also created to combine barcodes with the appropriate sample name in the  **./data** directory as a file called decradbarcodes1.txt. This barcode file and fastq files were then processed with STACKS using a sub function called *process_radtags* which demultiplexed the data while removing reads with ambiguous barcodes and radtags.

**directory**  ./data

**Barcode File**

decradbarcodes1.txt

##
### process_radtags output ###

This program then output fastq files containing all the reads for each sample based on the barcode into **./samples**. 

**directory**  ./samples

**processed fastq files**

|  Files Produced  |   |                  |   |                  |
|:----------------:|---|------------------|---|------------------|
| sample_CCCTAA.fq |   | sample_GGTTTG.fq |   |                  |
| sample_AAACGG.fq |   | sample_CCGAGG.fq |   | sample_GTAAGT.fq |
| sample_AACGTT.fq |   | sample_CCGCAT.fq |   | sample_GTATCC.fq |
| sample_AACTGA.fq |   | sample_CCTAAC.fq |   | sample_GTCATC.fq |
| sample_AAGACG.fq |   | sample_CGAGGC.fq |   | sample_GTGCCT.fq |
| sample_AAGCTA.fq |   | sample_CGCAGA.fq |   | sample_GTGTAA.fq |
| sample_AATATC.fq |   | sample_CGCGTG.fq |   | sample_GTTGGA.fq |
| sample_AATGAG.fq |   | sample_CGGTCC.fq |   | sample_TAAGCT.fq |
| sample_ACAAGA.fq |   | sample_CGTCTA.fq |   | sample_TAATTC.fq |
| sample_ACAGCG.fq |   | sample_CGTGAT.fq |   | sample_TACACA.fq |
| sample_ACATAC.fq |   | sample_CTACAG.fq |   | sample_TACGGG.fq |
| sample_ACCATG.fq |   | sample_CTCGCC.fq |   | sample_TAGTAT.fq |
| sample_ACCCCC.fq |   | sample_CTGCGA.fq |   | sample_TATCAC.fq |
| sample_ACTCTT.fq |   | sample_CTGGTT.fq |   | sample_TCAAAG.fq |
| sample_ACTGGC.fq |   | sample_CTTATG.fq |   | sample_TCCTGC.fq |
| sample_AGCCAT.fq |   | sample_CTTTGC.fq |   | sample_TCGATT.fq |
| sample_AGCGCA.fq |   | sample_GAAATG.fq |   | sample_TCGCCA.fq |
| sample_AGGGTC.fq |   | sample_GAACCA.fq |   | sample_TCGGAC.fq |
| sample_AGGTGT.fq |   | sample_GACGAC.fq |   | sample_TCTCGG.fq |
| sample_AGTAGG.fq |   | sample_GACTCT.fq |   | sample_TCTTCT.fq |
| sample_AGTTAA.fq |   | sample_GAGAGA.fq |   | sample_TGAACC.fq |
| sample_ATAGTA.fq |   | sample_GATCGT.fq |   | sample_TGACAA.fq |
| sample_ATCAAA.fq |   | sample_GCAGAT.fq |   | sample_TGCCCG.fq |
| sample_ATGCAC.fq |   | sample_GCATGG.fq |   | sample_TGCTTA.fq |
| sample_ATGTTG.fq |   | sample_GCCGTA.fq |   | sample_TGGGGA.fq |
| sample_ATTCCG.fq |   | sample_GCGACC.fq |   | sample_TTATGA.fq |
| sample_CAAAAA.fq |   | sample_GCGCTG.fq |   | sample_TTCCGT.fq |
| sample_CAATCG.fq |   | sample_GCTCAA.fq |   | sample_TTCTAG.fq |
| sample_CACCTC.fq |   | sample_GGACTT.fq |   | sample_TTGAGC.fq |
| sample_CAGGCA.fq |   | sample_GGCAAG.fq |   | sample_TTTAAT.fq |
| sample_CATACT.fq |   | sample_GGGCGC.fq |   | sample_TTTGTC.fq |
| sample_CCATTT.fq |   | sample_GGGGCG.fq |   |                  |
| sample_CCCGGT.fq |   | sample_GGTACA.fq |   |                  |

A log file produced by the program was then moved from the samples directory to the data directory for backup. While no errors are produced from this run, it only produces fastq files with barcodes instead of sample names.

**directory** ./data

**process radtags log file**
process_ radtags.log

### Samples for Stacks Process ###

Fastq files produced from *process_radtags* were checked for quality. The top 10 samples containing more than 180k reads were then selected to run through Stacks process. Sample fastq files can be found in **./samples**.

**samples used**

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

*in all subsequent references to these samples, they be referred to as ID instead of mentioning every individual file*
##
### ustacks ###
First the samples were run through the *ustacks* function which assembled the loci for each sample producing a sample.tags.tsv file, then called for SNPs producing a sample.snps.tsv file, and finally determined haplotypes and alleles creating a sample.alleles.tsv. No errors were produced for *ustacks* as it needs no input file to discern populations. Files were placed into the directory **./ustacks**. This creates 30 files. You can see the statistics for each sample and the number of reads and snps for each below.

| **Sample** 	|  **Reads** 	| **Mean Coverage** 	|  **St Dev** 	|
|:------:	|:------:	|:-------------:	|:-------:	|
| CACCTC 	|  79749 	|    9.77419    	|  21.343 	|
| CCCTAA 	| 162821 	|    15.5762    	| 54.4303 	|
| GCTCAA 	| 415583 	|    35.3757    	| 110.388 	|
| GTGTAA 	| 447678 	|    37.4178    	|  132.4  	|
| ACATAC 	| 615296 	|    48.1594    	| 113.335 	|
| ACCATG 	| 367241 	|    30.7252    	| 128.328 	|
| ACCCCC 	| 416392 	|    35.7519    	| 154.377 	|
| CAAAAA 	|  41575 	|    7.34319    	| 31.5243 	|
| TACACA 	|  6152  	|    5.97252    	| 18.3384 	|
| CAGGCA 	| 101739 	|    12.8119    	| 65.4695 	|

**directory** ./ustacks

**Assembled Loci file**
ID.tags.tsv (10 files)

This file contains information Loci and sequence information. Column 1 contains SQL ID, Column 2 contains the sample ID, Column 3 contains the Locus ID, Column 7 contains Sequence Type, Column 8 contains the Stack component, Column 9 contains the Sequence ID, Column 10 contains the Sequence, Column 11 equals the Deleveraged Flag, Column 12 contains the Blacklisted Flag, Column 13 contains the Lumberjackstack Flag, Column 14 contains the Log likelihood. 

**SNP calls file**
ID.snps.tsv (10 files)

This file contains SNP information. Column 1 contains SQL ID, Column 2 contains the sample ID, Column 3 contains the Locus ID, Column 4 contains column info, Column 5 contains the type, Column 6 contains the Likelihood ratio, Columns 7-10 contain Ranks 1-4 (Majority Nucleotide, Alternative Nucleotide, Third alternative nucleotide, fourth alternative nucleotide).

**Haplotypes/Alleles file**
ID.alleles.tsv (10 files)

This file contains haplotype information. Column 1 contains SQL ID, Column 2 contains the sample ID, Column 3 contains the Locus ID, Column 4 contains the haplotype, column 5 has the percent of reads for the haplotype, and column 6 contains the number of reads with the haplotype. 

##
### cstacks output ###

A population map tab delimited file produced outside of STACKS created with sample name and population designation. This file was then applied with the files produced from *ustacks* to *cstacks* to produce catalogs of all loci, snps, and haplotypes for each designated population in files Population.catalog.tags.tsv, Population.catalog.snps.tsv, Population.catalog.alleles.tsv. *cstacks* produced no error in this run but due to the lack of a population file it grouped all the selected samples into a single population catalog. Due to this, analysis during *sstacks* assumes no differences between samples and does not create catalogs around each population. Moving forward this only allows for *sstacks* and *populations* to treat all samples as sourced from a single population. The catalogs were output to the directory **./ustacks.** Below is the basic information about the catalog produced. 

|   Sample  	| K-mers 	|  Loci 	|
|:---------:	|:------:	|:-----:	|
| catalog 1 	|  32481 	| 28771 	|

**directory** ./ustacks

**Loci catalog file**
batch_ 1.catalog.tags.tsv

This file contains all the same info as the individual Loci TSVs but is an amalgamation of all samples used for the catalog. 

**SNP catalog file**
batch_ 1.catalog.snps.tsv

This file contains all the same info as the individual snps TSVS but is an amalgamation of all samples used for the catalog. 

**Allele catalog file**
batch_ 1.catalog.alleles.tsv

This file contains all the same info as the individual alleles TSVS but is an amalgamation of all samples used for the catalog. 

##
### sstacks output ###

Finally these catalogs were then used to compare individual samples to the population catalogs using the *sstacks* function which produced a matches file sample.matches.tsv. *sstacks* produces matches.tsv files for each sample only compared to the single population file. These files were output to **./ustacks** Below you can see the information for the number of matches and haplotypes for each sample and the catalog. 

| Sample 	| Matches 	| Haplotypes 	|
|:------:	|:-------:	|:----------:	|
| CACCTC 	|   7498  	|    8274    	|
| CCCTAA 	|   9721  	|    10873   	|
| GCTCAA 	|  10983  	|    12330   	|
| GTGTAA 	|  11200  	|    12608   	|
| ACATAC 	|  11884  	|    13346   	|
| ACCATG 	|  11123  	|    12517   	|
| ACCCCC 	|  10873  	|    12278   	|
| CAAAAA 	|   5135  	|    5575    	|
| TACACA 	|   821   	|     905    	|
| CAGGCA 	|   7367  	|    8170    	|

**directory**  ./ustacks

**Matches file**
ID.matches.tsv (10 files)

This file contains information about the matches between the catalog and the individual files. 
Column 1 contains the SQL ID, Column 2 contains the Batch ID, Column 3 contains the Catalog ID, Column 4 contains the sample id, Column 5 contains the Locus ID, Column 6 contains the haplotype match, column 7 is the Stack Depth (number of reads contained in the locus that match the catalog), Column 8 is the log likelihood. 
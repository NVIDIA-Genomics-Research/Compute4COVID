# GPU-accelerated short read alignment using Parabricks 

Parabricks provides GPU-accelerated BWA for short-read alignment to a reference genome.


## Data

`data/MN908947/MN908947.fasta` is the reference genome for SARS-CoV-2.

## Run GPU-accelerated BWA

Any user can run the following command to execute GPU-accelerated BWA-MEM, co-ordinate sorting, and marking duplicates, assuming Parabricks is already installed.

```
pbrun fq2bam --ref data/MN908947/MN908947.fasta --in-fq sample_1.fastq.gz sample_2.fastq.gz --out-bam output.bam

```
# GPU-accelerated short read alignment using Parabricks 

Parabricks provides GPU-accelerated BWA for short-read alignment to a reference genome.


## Data

`data/MN908947/MN908947.fasta` is the reference genome for SARS-CoV-2 in FASTA format.

## Installation

Follow the installation guide at `https://www.nvidia.com/en-us/docs/parabricks/local-installation/`

## Run GPU-accelerated BWA

Once Parabricks is installed, the following command performs:
1. GPU-accelerated BWA-MEM
2. Co-ordinate sorting
3. Marking duplicates.

```
pbrun fq2bam --ref data/MN908947/MN908947.fasta --in-fq sample_1.fastq.gz sample_2.fastq.gz --out-bam output.bam

```
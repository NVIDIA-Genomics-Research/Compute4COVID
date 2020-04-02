# Assembly Polishing using Racon

[Racon](https://github.com/lbcb-sci/racon) is a GPU-accelerated polishing tool for assembly from long reads.

## Installation

Installation instructions for Racon are available at https://github.com/lbcb-sci/racon#installation.

## Data

Racon requires 3 files to generate a polished assembly - 

1. Read data (in `.fasta` or `.fastq` for, with or without compression)
2. Overlap information of reads to reference (in `.paf`, `.sam` or `mhap`)
3. Target/reference sequences (in `.fasta` or `.fastq` for, with or without compression)

Oxford Nanopore read for SARS-CoV-2 can be downloaded from https://sra-pub-src-1.s3.amazonaws.com/SRR10948550/HKU-SZ-002a.fastq.1

Reference sequence for the virus is available [here](../short_read_alignment/data).

## Usage

The following commands demostrate how to run a reference guided assembly using long read data and polishing.
The example requires `minimap2` to be available as well (https://github.com/lh3/minimap2).

```
minimap2 -x map-ont -t 12 MN908947.fasta HKU-SZ-002a.fastq > overlaps.paf
racon -c 4 -m 8 -x -6 -g -8 -w 500 -t 12 -q -1 HKU-SZ-002a.fastq overlaps.paf MN908947.fasta > assembled.fasta
```

# Base calling from ONT long reads using Bonito


[Bonito](https://github.com/nanoporetech/bonito) is a [Quartznet](https://arxiv.org/abs/1910.10261)-based Deep Learning basecaller for Oxford Nanopore long-read sequencing.

## Installation

```
pip install ont-bonito
```

## Data

The input data for bonito is in the form of one or more `.fast5` files containing the raw data output from the sequencer. 

We provide some example `.fast5` files from ONT sequencing of SARS-CoV-2 using the [ARCTIC](https://artic.network/ncov-2019) protocol, collected by the [CADDE project](https://www.caddecentre.org/covid19/) [Citation](http://virological.org/t/first-report-of-covid-19-in-south-america/409). This is located in the `data` directory.

To extract the data use the following command:

```
tar -xvzf data/SP1-3-fast5.tar.gz
```

## Basecalling

The `bonito basecaller` command is used to perform basecalling. The model is named `dna_r9.4.1` and is intended for DNA sequencing data sequenced using the R9.4.1 pore. Bonito currently does not include a model for direct RNA sequencing. The directory containing one or more .fast5 files is given as input.

```
bonito basecaller dna_r9.4.1 data/SP1-3-fast5 > basecalls.fasta
```
If you have a turing or volta GPU the `--half` flag can be used to increase performance.

The output is saved in `.fasta` format. If multiple `.fast5` files are supplied as input, all basecalled read sequences are present in the same output file.

```
head basecalls.fasta

>00e1904e-0c09-4673-be53-4d6e4ce9c997
ATCAGAATAGTGCCATGGGTGGCACGTTGAGAAGAATGTTAGTTTCTGGATTGAATGACCACATCTGGAACGCGTACGCGCAAACAGTCTGAAAGAAGCA
ATGAAATGAGCCACATCAAGCCTACAAGACAAGCCATTGCGATAGCAATTCCACCAGTGATCCAATTTATTCTGCAAACAGCAACCAAGCACAAAACAAG

```


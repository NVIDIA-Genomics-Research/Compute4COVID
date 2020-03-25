# Base calling from ONT long reads using Bonito


Bonito (https://github.com/nanoporetech/bonito) is a highly accurate deep learning basecaller for long-read DNA sequencing, using Oxford Nanopore devices.

## Installation

```
pip install ont-bonito
```

## Data

The input data for bonito is in the form of one or more .fast5 files containing the raw data output from the sequencer. 

We provide some example data is from ONT sequencing of the Dengue virus (obtained from https://www.eurosurveillance.org/content/10.2807/1560-7917.ES.2018.23.50.1800228). This is located in the `data` folder.

```
tar -xvzf data/Mapped_DENV_Rapid.tar.gz.1
```

## Basecalling

The `bonito basecaller` command is used to call bases. The model is named `dna_r9.4.1` and is intended for DNA sequencing data. Bonito currently does not include a model for direct RNA sequencing. The directory containing one or more .fast5 files is given as input.

```
bonito basecaller dna_r9.4.1 data/Mapped_DENV_Rapid > basecalls.fasta
```
If you have a turing or volta GPU the `--half` flag can be used to increase performance.

The output is saved in .fasta format. If multiple .fast5 files are supplied as input, all basecalled read sequences are present in the same output file.

```
head Mapped_DENV_Rapid.fasta 

>9226e616-1222-4141-9e09-7217155f623e
TTTCGCATTTAATATCGTGAAACGCTTTCGCGTTTTTCGTGCGCCGCTTCACTATGGGATTGGCTGTTATCAATCTCCCATTCTGGGTTACTCCTTTTCA
TCTAGGTCGAAAAGGGATCTTGCATGGTGCATCTGTTCCTTCGTATTTAATCTGCACACTAAGAGCAGGTTCCATGCTGGGTCTCGGCTCCACTTCTTTC
TCTAGCTTGAACAAACCTATTGCACATCACATATGACATCCCTTTTAGAGTCAGTTTATCCATCTTTTGATCTACATTTTCAAGTGTCCTGCAAAAATTG
TTGTCGTTCCAGACGTTTGGATTTCCGTCATCCGGTCAACACATTGCCATTGTCACTCCTTCTTGTGATCCTAATTTCGACTACTTCCTGCTTCTCACAT
GAGCTACATCTAAATGTCACCGGCAAATCTTGTCTGCTCCAAGTTTCTTGTGATGTTGAAGCTCGAGGTCCAAGGCAGTGGTAGGTCTAGAAACCTGTGT
TTGTGGACTAGCCATGATTTTTCTTTCATTATTAACAGCTTTCATTTCATTAGTCTAGTCTGTTCTGGTGAACTTAATCCAATGTAAACTCCGTAGTGTC
```


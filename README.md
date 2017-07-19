# var_scanner

## Introduction  
Multi-locus sequence typing (MLST) is a highly discriminating *Candida albicans* strain typing method. It is usually applied to one colony per patient sample. However, multiple strains can coexist in the same site in a patient. We therefore developed 100+1 NGS-MLST, a next generation sequencing (NGS) modification of the existing *C. albicans* MLST method. It analyzes DNA extracted from a pool of 100 colonies from a sample plus DNA from one colony and bioinformatically infers the genotypes present and their frequency. It does so at a sequencing cost, per patient sample, four times lower than that of conventional MLST.  For the directly typed single colonies its discriminating power is 0.998, comparable to that of conventional MLST. Its predictions of the ratio of different strains in a sample were fairly accurate - within 14±16% of the ratio between the numbers of colonies from two known strains combined to generate DNA pools for testing the method’s accuracy. Details of our proof of principle experiment using 100+1 NGS-MLST can be found in the our recent publication XXXX. 

To cite var_scanner:
XXXX *et al*:DIO:XXXXX  

## Requirements  
This scripts are writen in pure python and should only require python 2.7 install on the machine.  

## Installation  
Create a base directory and clone the repo into.  
```bash
mkdir var_scanner && cd var_scanner   
git clone XXXXX   
```

# setup the directories
mkdir final_genotpyes/
mkdir final_sequences/
mkdir genotype_data/

## File and folder/structure required  
The following file/folder structure is required to run var_scanner. These should exist if you followed the installion instructions shown above:  
<pre>
BASE_DIR  -  samples/  # contains demultiplexed samples in directories named after the sample name
          -  final_genotpyes/  # data Xxxx
          -  final_sequences/ # data xxx
          -  genotype_data/  # data xxx
          -  reference_mlst/  # reference MLST sequence used for alignment
          -  create_sequences.py  # script to create infered fasta files for alignment
          -  extract_seq_from_sheet.py  # script to extract sequences from data sheet
          -  run_aligner.py  # alignment script
          -  demultplex.py  # demultiplex script that saves sequence files in folders named after the sample names
          -  genotyper_iter.py  # genotyper script
       
</pre>

## Running var_scanner (gui version)
The GUI is under current development.  

## Running var_scanner (non-gui version)

1. Either use the included demultplex.py script to demultplex your samples into directories named after the sample and place these in the BASE_DIR/sample directory. ie 


If sequences need demultiplexing then run the demultiplex.py.


usage:  
python demultplex.py 12-0039_S10_L001_R2_001.fastq \
  forward_primers.txt reverse_primers.txt | tee -a log.txt

I removed the len(14) for loop that only reported non-ref calls.
This was because we wanted all the tables to be the same number
of rows.

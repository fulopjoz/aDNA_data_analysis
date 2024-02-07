# Ancient mtDNA Analysis Project

## Overview

This project involves analyzing mitochondrial DNA (mtDNA) from ancient samples. It focuses on identifying sequences that are missing from the AmtDB database but found in an external "mt dataset," as well as sequences that are present in the "mt dataset" but not registered in AmtDB at all. The aim is to enhance the completeness and diversity of the AmtDB database by retrieving these missing sequences and incorporating entirely new data.

## Setup

The analysis requires Python 3.8 along with several libraries including BioPython, Pandas, and NumPy. Use Conda to set up a virtual environment for running the analysis tools:

```bash
conda create -n ancient_dna_env python=3.8 biopython pandas matplotlib numpy jupyter ipython scipy seaborn -y
```

## Usage

After setting up the environment, run the provided Jupyter notebooks or Python scripts within the Conda environment to perform the analysis. The scripts will compare sequences from the "mt dataset" against the AmtDB database, identify missing sequences, and attempt to retrieve them.
Output Files

## The analysis generates several output files located in the output/ directory

* sequences_missing_in_AmtDB.fasta: FASTA file containing sequences that are referenced in the AmtDB metadata but whose sequence data are missing from AmtDB. These sequences were found in the external "mt dataset."
* metadata_for_sequences_missing_in_AmtDB.csv: Metadata for the sequences in sequences_missing_in_AmtDB.fasta, detailing the archaeological and genetic context of each sequence.
* sequences_not_present_in_AmtDB.fasta: FASTA file including sequences present in the "mt dataset" but not found in AmtDB, indicating they are unique additions to the database.
* metadata_for_sequences_not_present_in_AmtDB.csv: Corresponding metadata for the sequences in sequences_not_present_in_AmtDB.fasta, providing detailed background information for these new samples.

## Structure

* data/: Contains the input CSV and FASTA files used for the analysis.
* output/: Stores the output files, including newly identified FASTA sequences and their metadata.
* Various analysis scripts and Jupyter notebooks used for processing and analyzing the mtDNA data.

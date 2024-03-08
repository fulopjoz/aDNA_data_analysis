# Ancient DNA Analysis Pipeline

## Overview

This repository contains a Jupyter notebook implementing three pipelines for the analysis of ancient DNA (aDNA) data, focusing on integrating and analyzing datasets from AmtDB and the Allen Ancient DNA Resource (AADR). These pipelines are designed to identify missing sequences, extract and save specific sequences, and match and save metadata for comprehensive analysis.

## Pipeline Overview

### 1. Initial Pipeline

The first approach involves creating directories, loading data from AmtDB and AADR, identifying missing sequences, and extracting and saving these sequences along with their metadata.

#### Key Features

- Directory creation for output data
- Loading metadata and sequence IDs from AmtDB and AADR datasets
- Identifying missing sequences within AmtDB
- Extracting sequences from the mitochondrial dataset available in AADR not present in AmtDB
- Matching and saving metadata for the identified sequences

## Installation

### Dependencies

- Python 3.8+
- Biopython
- Pandas
- Other dependencies as required by specific analyses in the pipelines

To set up the environment and install the required packages:

```shell
conda create -n ancient_dna_env python=3.8 biopython pandas -y
```

## Usage

To run the pipelines, navigate to the notebook directory and launch Jupyter Notebook:

```shell
jupyter notebook
```

Then, open the provided .ipynb file and execute the cells in order.

## Input Data

- AmtDB: Metadata and sequences should be placed in data/amtDB. Expected files include amtdb_metadata.csv and a FASTA file with sequences.
- AADR Mitochondrial Dataset: Should be placed in data/mitogenomes_reich, including a FASTA file for sequences and a .anno file for metadata.

## Output Data

Outputs are saved in the output directory, including:

- Sequences found missing in AmtDB but present in AADR, saved as FASTA files.
- Metadata for the missing sequences, saved in CSV format.
- Sequences present in AADR but not in AmtDB, with their metadata.

## Results Summary

The pipelines identify and process sequences missing in AmtDB or uniquely present in AADR, facilitating comprehensive analysis and integration of these ancient DNA datasets.

## Second Approach: Utilizing MASTER ID for AADR Analysis

This section of the pipeline introduces functions for loading IDs from various file types, identifying missing sequences within the AmtDB dataset, and identifying sequences present in the AADR dataset but not in AmtDB. It leverages "Master ID" from the AADR for a more targeted approach in matching sequences and metadata across datasets.

### Key Functions

- `load_ids_from_csv`, `load_ids_from_anno`, `load_ids_from_fasta`: Functions for loading IDs from CSV, annotation files, and FASTA files, respectively.
- `find_missing_sequences`: Identifies IDs that are expected but not present in the FASTA files.
- `extract_and_save_sequences`: Extracts sequences matching specified IDs from FASTA files and saves them.
- `match_and_save_metadata_amtdb` and `match_and_save_metadata_aadr`: Matches metadata for specified IDs and saves it to CSV files, tailored for AmtDB and AADR datasets, respectively.

### Processing Steps

1. **ID Loading**: Loads all IDs from AmtDB and AADR databases, including both metadata and FASTA file IDs.
2. **Missing Sequence Identification**: Identifies sequences missing within AmtDB and those present in AADR but not in AmtDB.
3. **Sequence and Metadata Extraction**: Extracts sequences based on the identified missing IDs and matches metadata for these sequences using "Master ID" for AADR.

### Results

- **920 sequences** were identified as missing internally within AmtDB.
- **2996 sequences** were identified as not present in AmtDB but available in AADR.
- **404 sequences** were extracted and saved, representing those missing internally in AmtDB but found in AADR, with **561 metadata records** matched and saved.
- **3004 sequences** not present in AmtDB were extracted and saved, with their corresponding metadata records.

### Outputs

- Sequences missing internally in AmtDB but found in AADR are saved in `output/sequences_missing_internally_in_AmtDB_masterID.fasta` with metadata in `output/metadata_for_sequences_missing_internally_in_AmtDB_masterID.csv`.
- Sequences not present in AmtDB are saved in `output/sequences_not_present_in_AmtDB_masterID.fasta` with metadata in `output/metadata_for_sequences_not_present_in_AmtDB_masterID.csv`.

## Third Approach: Utilizing GENETIC ID for AADR Analysis

This section focuses on a refined strategy for analyzing ancient DNA data by leveraging "Genetic ID" from the AADR dataset. This approach is designed to improve the specificity and accuracy of matching sequences to metadata, facilitating a deeper analysis of the genetic information available in these ancient datasets.

### Key Functions 2

- `load_ids_from_csv`, `load_ids_from_anno`, `load_ids_from_fasta`: These functions are tailored for loading IDs from CSV files, annotation files, and FASTA files, respectively, using "Genetic ID" as the key identifier for the AADR data.
- `find_missing_sequences`: Identifies and lists IDs expected in the dataset but missing from the FASTA sequence files.
- `extract_and_save_sequences`: Extracts sequences that match specified IDs from FASTA files and saves them for further analysis.
- `match_and_save_metadata_amtdb` and `match_and_save_metadata_aadr`: These functions match metadata for specified IDs against the AmtDB and AADR datasets and save the matched metadata to CSV files.

### Processing Steps 2

1. **ID Loading**: Load all relevant IDs from both AmtDB and AADR databases, focusing on metadata and FASTA file IDs using "Genetic ID".
2. **Missing Sequence Identification**: Identify sequences that are missing within AmtDB and those that are present in AADR but not in AmtDB, enhancing the comprehensiveness of the dataset analysis.
3. **Sequence and Metadata Extraction**: Extract sequences based on identified missing IDs and match metadata for these sequences, emphasizing the utility of "Genetic ID" for nuanced data integration.

### Results 2

- Identified **920 sequences missing internally within AmtDB** and **2996 sequences not present in AmtDB but available in AADR**.
- Extracted and saved **404 sequences missing internally in AmtDB** found in AADR, with **434 metadata records** matched and saved.
- Additionally, **3004 sequences not present in AmtDB** were extracted and saved, with their corresponding metadata records.

### Outputs 2

- Sequences missing internally in AmtDB but found in AADR are saved in `output/sequences_missing_internally_in_AmtDB_geneticID.fasta` with metadata in `output/metadata_for_sequences_missing_internally_in_AmtDB_geneticID.csv`.
- Sequences not present in AmtDB are saved in `output/sequences_not_present_in_AmtDB_geneticID.fasta` with metadata in `output/metadata_for_sequences_not_present_in_AmtDB_geneticID.csv`.

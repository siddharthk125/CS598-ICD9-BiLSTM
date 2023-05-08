# Reproduction Instructions

This repository contains the code to reproduce the results presented in the paper "BiLSTM-based ICD-9 Code Assignment from Clinical Text". The code was originally implemented in Python 3.7.6 with PyTorch 1.6.0.

## Citation to the Original Paper

If you use the code or results presented in this repository, please cite the original paper:

    Smith, M., Jones, J., & Doe, J. (2021). BiLSTM-based ICD-9 Code Assignment from Clinical Text. Journal of Medical Informatics, 15(2), 123-130.

## Dependencies

The code requires the following dependencies:

- Python 3.x
- PyTorch 1.6.0
- Pandas
- NumPy
- Scikit-learn
- NLTK

These dependencies can be installed using the following command:

`!pip install torch==1.6.0 pandas numpy scikit-learn nltk`


## Data Download Instructions

The original paper used the MIMIC-III dataset, which can be obtained from https://mimic.mit.edu/. Due to the restrictions on the use of the MIMIC-III dataset, we cannot provide the data directly in this repository. However, the code can be run with any dataset that is formatted in the same way as the MIMIC-III dataset. 

Once the data is obtained, the `data` directory should contain the following files:

- `notes_train.csv`: Training set containing clinical notes and corresponding ICD-9 codes.
- `notes_val.csv`: Validation set containing clinical notes and corresponding ICD-9 codes.
- `notes_test.csv`: Test set containing clinical notes and corresponding ICD-9 codes.

## Preprocessing Code + Command

Preprocessing is done using MetaMapLite. In order to preprocess from MetaMapLite, download MetaMapLite jar and install it using https://lhncbc.nlm.nih.gov/ii/tools/MetaMap/run-locally/MetaMapLite.html. Then to get the keywords, run the following command -
`./metamaplite.sh --indexdir=Path/To/MIMICIII/dataset/document-id.txt --restrict_to_sts=sosy,dsyn,neop`


This command will preprocess the data and save the MetaMap file to the corresponding directory.


# Reproduction Instructions

This repository contains the code to reproduce the results presented in the paper "A disease inference method based on symptom extraction and bidirectional Long Short Term Memory networks"

## Citation to the Original Paper

If you use the code or results presented in this repository, please cite the original paper:

   ```Donglin Guo, Guihua Duan, Ying Yu, Yaohang Li, Fang-Xiang Wu, Min Li, A disease inference method based on symptom extraction and bidirectional Long Short Term Memory networks, Methods, Volume 173, 2020, Pages 75-82,ISSN 1046-2023```

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

- `NOTEEVENTS.csv`: Contains the clinical notes associated with a Hospital Admission ID (`HADMID`), which is used as the predictor
- `DIAGNOSES_ICD.csv.gz`: Contains the ICD9 code of the disease that has been diagnosed for a patient in a given visit marked by a `HADMID`

## Preprocessing Code + Command

Preprocessing was done using MetaMapLite. We used MetaMapLite over MetaMap, due to time constraint and the limitation in speed in MetaMap.
  In order to preprocess from MetaMapLite, download MetaMapLite jar and install it using https://lhncbc.nlm.nih.gov/ii/tools/MetaMap/run-locally/MetaMapLite.html. Then to get the keywords, run the following command -
   
  `./metamaplite.sh --indexdir=Path/To/MIMICIII/dataset/document-id.txt --restrict_to_sts=sosy,dsyn,neop`

  
This command will preprocess the data and save the MetaMap file to the corresponding directory.


This command will evaluate the model on the test set and save the evaluation results to the `document-id.mmi` file.

## Table of Results
The study was conducted on 2 datasets -
1. Dataset filtered containing top 50 ICD9 codes
2. Dataset filtered containing top 100 ICD9 codes
### Top 50 ICD9 codes
These following results were obtained by training the model on the MIMIC-III dataset filtered with top 50 ICD9 diseases.
| Metric       | Value   |
|--------------|---------|
| Micro Precision    | 0.454   |
| Micro Recall       | 0.571   |
| Micro F1-Score     | 0.506   |
| Micro AUC     | 0.820   |
| Macro Precision    | 0.413   |
| Macro Recall       | 0.422   |
| Macro F1-Score     | 0.418   |
| Micro AUC     | 0.752   |

### Top 100 ICD9 codes
These following results were obtained by training the model on the MIMIC-III dataset filtered with top 100 ICD9 diseases.
| Metric       | Value   |
|--------------|---------|
| Micro Precision    | 0.446   |
| Micro Recall       | 0.496   |
| Micro F1-Score     | 0.467   |
| Micro AUC     | 0.775   |
| Macro Precision    | 0.385   |
| Macro Recall       | 0.405   |
| Macro F1-Score     | 0.395   |
| Micro AUC     | 0.691   |


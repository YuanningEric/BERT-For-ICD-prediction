# Description
This repository contains the codes that fine tune the BERT model for ICD code prediction using patient discharge summaries. Pre-trained clinical BERT can be found in this repository: `https://github.com/EmilyAlsentzer/clinicalBERT`.

## Before Your Start
We provided a `environment.yml` file for the prerequisite packages. 


## Dataset

Datasets were extracted from the MIMIC III database. We used discharge summary with diagnostic ICD codes of each patient as our training data. Specificlly, we download three seperate datasets: NOTEEVENTS.csv, D_ICD_DIAGNOSES.csv, D_ICD_PROCEDURES.csv. 

## Data Preprocessing / Tokenization / Word Embeddings

We provided a Jupyter notebook written in Python for data preprocessing, which can be found in the *notebooks_preprocessing_evaluation* folder. To improve the preprocessing efficiency, we also provided a PySpark version.

## Input to the BERT Model
We used the following output from the previous data preprocessing as input to the BERT model full label prediction: 
```
train_full.csv
test_full.csv
dev_full.csv
```
For top50 ICD-9 code prediction, we need following 3 datasets,
```
train_50.csv
test_50.csv
dev_50.csv
```
This datasets are also availabe by downloading through following link
```
https://drive.google.com/open?id=1-1PteVz3SlFF-92c5UUR35JIiSkknSbS
```

## Model Fine Tunig
In jupyter notebook `clinical_bert_ICD_cpu.ipynb` and `clinical_bert_ICD_cpu-top50.ipynb`, training function has been implemented by running `fit()` function. Run this function to reproduce the fine tuning process. 

This process takes quite amount of time (a few hours based on GPU utilization), so you can downloaded fine tuned model through following link
```
https://drive.google.com/open?id=1R3QUxY7yDnUbfpddYHaUKeTVpDDaMybd
```
## Model Evaluation
At the end, run evaluation fuction under **Model Evaluation** section and obtain the evaluation results on test dataset. We established the following evaluation matrics: AUC, recall, F1 score, Precision@n.

## References
https://github.com/EmilyAlsentzer/clinicalBERT

## Skip gram results
We also produced produced results using skip gram Word2Vec embeddings instead of continuous bag of words embedding just as a comparison

Exact same pre-processing/script runs were executed simply by replacing word_embeddings.py in original github repository with our word_embeddings.py

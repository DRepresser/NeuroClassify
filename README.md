# Neuropeptide Classification using ESM Embeddings

This repository contains the implementation and methodology for classifying neuropeptides from non-neuropeptides using Evolutionary Scale Modeling (ESM) embeddings and machine learning models. The workflow includes data preparation, exploratory data analysis (EDA), feature extraction, model training, and evaluation.

## Introduction

Neuropeptides are biologically active molecules that play critical roles in communication within the nervous system. Distinguishing neuropeptides from non-neuropeptides is an important task for understanding protein functionality. This repository employs machine learning techniques and protein sequence embeddings derived from ESM to build a robust classification model.

## Methodology

### 1. Data Gathering

Data was collected from:

- [NeuropredV2](http://isyslab.info/NeuroPepV2)
- [UniProt](https://www.uniprot.org)
- [ASYNPepDB](https://asynpepdb.ppmclab.com/)
- [NeuroPedia](https://asynpepdb.ppmclab.com/)
- [NeuroPred-PLM](https://github.com/ISYSLAB-HUST/NeuroPred-PLM)
- [Figshare FASTA Dataset](https://figshare.com/articles/dataset/FASTA_files_of_protein_and_predicted_neuropeptide_sequences_zip/8379326/1?file=15657851)

The dataset consists of:
- ~3 million neuropeptides
- ~11 million non-neuropeptides

The dataset was downsampled and balanced to 100,000 sequences for training and evaluation.

### 2. Data Preprocessing

- Filtered sequences by length and removed sequences with excessive repeat amino acids.
- Clustered sequences using CD-HIT to reduce redundancy.
- Sampled one sequence per cluster to retain diverse and representative data.

### 3. Exploratory Data Analysis (EDA)

Key insights include:
- Label distribution
- Sequence length distribution by class
- Amino acid frequency analysis

### 4. Feature Extraction

- Embeddings: Extracted 1280-dimensional embeddings for each sequence using ESM.
- Dimensionality Reduction: Reduced feature size to 128 dimensions using PCA.

### 5. Model Training

Models used:
- Support Vector Classifier (SVC)
- Logistic Regression
- LightGBM Classifier (LGBMClassifier)
- Random Forest
- Gradient Boosting Classifier
- etc.

Hyperparameter tuning was performed using Grid Search with 5-fold cross-validation.

### 6. Model Evaluation

Metrics used to evaluate the models:
- Accuracy
- Precision
- Recall
- F1-Score
- Confusion Matrix

Results

The best-performing model (CumlSVC) achieved:
- CV Score (Accuracy): 0.712
- Accuracy: 0.709
- Precision: 0.710
- Recall: 0.709
- F1-Score: 0.709
- Confusion Matrix:

|                  | Predicted Positive | Predicted Negative |
| ---------------- | :----------------: |:------------------:|
| Actual Positive  |        7482        |        2596        |
| Actual Negative  |        3219        |        6703        |

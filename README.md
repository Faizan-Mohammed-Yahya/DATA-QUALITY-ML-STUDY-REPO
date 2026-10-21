# DATA-QUALITY-ML-STUDY-REPO
An ambitious study on how data quality affects machine learning performance across two domains . 

This project investigates how data-quality problems affect a simple machine-learning model. 
It uses logistic regression so the main focus remains on the data rather than model complexity. 


# Research question

How do missing values, duplicate records, outliers, inconsistent values, and class imbalance affet classification performance, and do their effects differ across domains (industries like medicine, finance, and manufacturing data) ?


# Project phases

Phase 1 - Adult Income: has a binary classification target. Which is to predict whether a person's annual income is above $50,000. 
Phase 2 - Chronic Kidney Disease: predicts whether a healthcare record is labelled CKD. 

Each phase compares the same seven conditions: 

E0: original baseline
E1: missing-value treatment 
E2: duplicate treatment
E3: Outlier treatment 
E4: invalid or inconsistent value treatment 
E5: class-imbalance treatment 
E6: combined selected pipeline 


# Datasets 

The unchanged dataset files are in the datasets folder.

Adult Income: https://archive.ics.uci.edu/dataset/2/adult
Chronic Kidney Disease: https://archive.ics.uci.edu/static/public/336/data.csv


Both datasets are published by the UCI Machine Learning Repository under the CC BY 4.0 licence.

# Repo Contents 
The final report is in Word format.
The experiment was conducted in Google Colab / Jupyter notebooks for both the phases.

The software used were: Python 3 with pandas, NumPy, Matplotlib, scikit-learn and threadpoolctl.


# Google Colab 
Open a notebook in Google Colab. Its dataset-loading cell diplays a file upload box when the required dataset file is not already present:
Phase 1 uses adult.data and adult.names
Phase 2 uses ckd.csv

The notebooks create their result CSV files and chart images in the Colab runtime session. 

# *Reproducibility*

The main comparison uses random seed 42. Seeds 43 and 44 provide a small sensitivity check. The train/test split is grouped to prevent gfeature-identical records from appearing on both sides. Preprocessing values and outlier limits are learned from training rows only. 

The supplied notebooks were executed from beginning to end during testing. Their main metrics exactly match the result tables and report

# Main Finding. 
The strongest change, atleast for phase 1 came from balanced class weights. The recall increased substantially, but precission decreased. In phase 2, outlier clipping improved one already strong test split but the gain was not stable across the additional splits. This suggests that data-quality effects are context-dependent. 


# Limitation Acknowledgement 

The project is restricted to two datasets, and ONE simply model (logistic regression) as opposed to a 19-model study conducted by Mohammed et al. https://arxiv.org/pdf/2207.14529
Secondly the results describe these experiments. They are not UNIVERSAL rules. 

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


# Main Finding. 
The strongest chanfe, atleast for phase 1 came from balanced class weights. The recall increased substantially, but precission decreased. 


# Limitation Acknowledgement 

The project is restricted to two datasets, and ONE simply model (logistic regression) as opposed to 19-model such as one study conducted by Mohammed et al. https://arxiv.org/pdf/2207.14529

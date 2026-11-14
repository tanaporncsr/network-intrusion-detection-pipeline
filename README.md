# Data Engineering Pipeline for Network Intrusion Detection Using the NSL-KDD Dataset

## Project Overview
This project focuses on designing a data engineering pipeline to prepare and process network traffic data from the NSL-KDD dataset for network intrusion classification.

The pipeline covers data quality checking, data cleaning, feature selection, feature engineering, and preprocessing. A Random Forest model is used to evaluate the impact of the pipeline on classification performance.

## Objectives
- Explore and assess the quality of the NSL-KDD dataset.
- Clean and prepare data for further analysis.
- Apply feature selection and feature engineering techniques.
- Evaluate how different pipeline stages affect classification performance.

## Dataset
The project uses the **NSL-KDD dataset**, which contains network connection records.

- **KDDTrain+:** 125,973 records
- **KDDTest+:** 22,544 records
- **Features:** 41 input features, along with class labels and difficulty levels.
- **Target classes:** Normal, DoS, Probe, R2L, and U2R.

## Data Engineering Pipeline
1. **Data Extraction:** Load the training and testing datasets and assign column names.
2. **Data Quality Check:** Examine missing values, duplicate records, constant features, skewness, and class distribution.
3. **Data Cleaning:** Remove duplicate records and constant features.
4. **Feature Selection:** Use correlation analysis to remove highly correlated features (|r| > 0.95), reducing the number of features from 40 to 34.
5. **Feature Engineering:** Create additional features using ratio calculations, log transformations, and error-rate combinations.
6. **Preprocessing:** Apply One-Hot Encoding to categorical features and scaling when required.

## Model Evaluation
A Random Forest classifier is used as a representative model to evaluate the pipeline. An ablation study is conducted to compare model performance across different feature configurations.

The best-performing setup, using 34 selected features, achieved a **Test Macro F1-score of 0.680**.

The experiments also showed that adding more features did not always improve generalization. One setup with 8 additional experimental features achieved a training accuracy of 0.992, while its test F1-score decreased to 0.627.

## Tools & Technologies
- Python
- Pandas, NumPy
- Scikit-learn
- Matplotlib
- Google Colab

## Web Application — NetGuard
A Streamlit web application was developed to demonstrate the network intrusion classification system. It provides three main features:

- **Threat Detection:** Enter network connection details manually and get a prediction with its confidence level, severity, and suggested action.
- **Batch Analysis:** Upload network data files in CSV, TXT, TSV, Excel, JSON, or Parquet formats to classify multiple connections at once. Users can review, filter, and download the prediction results.
- **Threat Dashboard:** View a summary of checked connections, detected threats, threat rates, severity levels, and recent analysis history.

The application uses the trained model developed in this project. Uploaded files must contain data in a format compatible with the model's input features.

## Project Scope
This was a collaborative group project for the Data Engineering course. Team members shared responsibilities across data cleaning, feature engineering, and model development, then integrated their work into the final pipeline and web application.

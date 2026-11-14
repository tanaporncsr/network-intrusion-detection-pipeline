# Data Engineering Pipeline for Network Intrusion Detection Using the NSL-KDD Dataset

## Project Overview
This project focuses on designing a Data Engineering Pipeline to prepare and process network traffic data from the NSL-KDD dataset for network intrusion classification.

The pipeline covers data quality assessment, data cleaning, feature selection, feature engineering, and preprocessing. A Random Forest model was used to evaluate the processed data and examine how different pipeline stages affected classification performance.

## Objectives
- Assess and improve the quality of network traffic data.
- Prepare data for network intrusion classification.
- Apply feature selection and feature engineering techniques.
- Evaluate the impact of different data preparation steps on model performance.
- Develop a web application to demonstrate the classification results.

## Dataset
The project uses the **NSL-KDD dataset**, which contains network connection records labeled as either normal traffic or different types of attacks.

| Dataset | Number of Records |
|---|---:|
| KDDTrain+ | 125,973 |
| KDDTest+ | 22,544 |

The original attack labels were grouped into five categories:
- Normal
- DoS (Denial of Service)
- Probe
- R2L (Remote to Local)
- U2R (User to Root)

## Data Engineering Pipeline

The pipeline consists of the following stages:

1. **Data Extraction:** Load the KDDTrain+ and KDDTest+ datasets and assign column names.
2. **Data Quality Assessment:** Check missing values, duplicate records, constant features, skewness, and class distribution.
3. **Data Cleaning:** Remove duplicate records and constant features.
4. **Feature Selection:** Analyze feature correlations using the training data and remove highly correlated features with an absolute correlation greater than 0.95.
5. **Feature Engineering:** Create additional features, including byte ratios, log-transformed values, error-rate features, and aggregated suspicious activity indicators.
6. **Preprocessing:** Apply One-Hot Encoding to categorical features and scaling where required by the model.
7. **Model Evaluation:** Use Random Forest to evaluate the processed data and compare different pipeline configurations.

## Model Evaluation

An ablation study was conducted to examine how different data preparation stages affected model performance.

- The feature selection process reduced the number of features from 40 to 34.
- The configuration using 34 features achieved the highest Test Macro F1-score of **0.680**.
- Adding eight experimental features resulted in a training accuracy of **0.992**, while the Test F1-score decreased to **0.627**, indicating a possible generalization issue.

These results highlight the importance of evaluating feature engineering techniques based on their performance on unseen data.

## Web Application — NetGuard

A Streamlit web application was developed to demonstrate the network intrusion classification system. [Try the App](https://network-intrusion-detection-pipeline-b46g4ns3jh582j5oqbwpha.streamlit.app)

### 1. Threat Detection
Users can enter network connection details manually and receive a prediction with its confidence level, severity, and suggested action.

![Streamlit Application Screenshot](images/threat-detection-screenshot.png)

### 2. Batch Analysis
Users can upload network data files in supported formats to classify multiple connections. The results can be reviewed, filtered, and downloaded.

![Streamlit Application Screenshot](images/batch-analysis-screenshot.png)

### 3. Threat Dashboard
The dashboard provides an overview of analyzed connections, detected threats, threat rates, severity levels, and recent analysis history.

![Streamlit Application Screenshot](images/threat-dashboard-screenshot.png)

The application uses the trained model developed in this project. Uploaded files must contain data in a format compatible with the model's input features.

## Tools & Technologies
- **Programming Language:** Python
- **Data Processing:** Pandas, NumPy
- **Machine Learning:** Scikit-learn
- **Data Visualization:** Matplotlib
- **Web Application:** Streamlit
- **Development Environment:** Google Colab

## Project Scope
This was a collaborative group project for the Data Engineering course. Team members shared responsibilities across data cleaning, feature engineering, and model development, then integrated their work into the final pipeline and web application.

The project focuses on data preparation and model evaluation using the NSL-KDD dataset. The web application serves as a demonstration of the developed classification system rather than a production-ready intrusion detection system.

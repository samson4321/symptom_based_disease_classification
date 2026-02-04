Disease Prediction Using Machine Learning (Kaggle Dataset)
📌 Project Overview

This project explores the use of machine learning models to predict diseases based on patient demographic information and reported symptoms.
The primary goal is to evaluate whether symptom-based data alone is sufficient for accurate multi-class disease classification.

The dataset used in this project was sourced from Kaggle and contains patient records with various diseases and associated symptoms.

📂 Dataset Description

Source: Kaggle Healthcare Dataset

Type: Structured tabular data

Target Variable: Disease (multi-class classification)

Input Features

Age

Gender

Reported Symptoms (text-based, converted to binary features)

Removed Columns

Patient_ID: Identifier only, no predictive value

Symptom_Count: Redundant after symptom encoding

🔄 Project Workflow
1. Data Loading

Dataset loaded from CSV format

Initial inspection performed to understand structure and data types

2. Data Preprocessing

The following steps were applied:

Handling of categorical variables using one-hot encoding

Splitting symptom strings into individual symptom indicators

Train-test split (75% training, 25% testing) with stratification

Feature scaling prepared for distance-based models

🧠 Models Implemented
K-Nearest Neighbors (KNN)

Tested with multiple values of K (3, 5, 7, 9, 11)

Suitable for small and well-separated feature spaces

Random Forest Classifier

Ensemble-based model capable of handling non-linear relationships

Used as a benchmark against KNN

📊 Results
Model Accuracy
Model	Accuracy
KNN (best K)	~3.5%
Random Forest	~3.0%
Classification Report Summary

Precision, recall, and F1-scores are consistently low across all disease classes

No individual disease category achieves strong predictive performance

Overall accuracy is close to random guessing

🧪 Interpretation of Results

The extremely low accuracy (~3%) indicates that the models are unable to learn meaningful patterns from the available data.

This behavior can be interpreted as follows:

The dataset contains many disease classes, making the classification task highly complex

Many diseases share similar or identical symptoms

Symptom-based features alone do not provide sufficient discriminatory power

The models effectively perform at random-guess level

This outcome highlights a fundamental limitation of the dataset rather than an implementation error.

❗ Key Challenges Identified

High Number of Classes

Multi-class classification with dozens of diseases increases difficulty

Symptom Overlap

Similar symptoms appear across multiple diseases

Sparse Feature Representation

One-hot encoding of symptoms leads to high-dimensional sparse data

Lack of Strong Medical Features

No lab results, medical history, or severity indicators included

🚀 Way Forward: How This Can Be Improved

To address these challenges, future work may include:

🔧 Data Improvements

Grouping similar diseases into broader categories

Removing rare or low-frequency symptoms

Incorporating additional medical features (e.g., test results)

🤖 Model Improvements

Applying class balancing techniques (e.g., SMOTE)

Using advanced models such as Gradient Boosting (XGBoost, LightGBM)

Performing hyperparameter tuning with GridSearchCV

📈 Evaluation Improvements

Using top-k accuracy instead of strict accuracy

Applying confusion matrix analysis to identify systematic misclassifications

📌 Conclusion

This project demonstrates the limitations of symptom-based disease prediction using standard machine learning models.
While the achieved accuracy is low, the experiment provides valuable insights into the challenges of real-world medical classification tasks.

Understanding why a model fails is a crucial step toward building more reliable and responsible machine learning systems.

🧾 Notes

This project is intended for educational and experimental purposes only and should not be used for real medical diagnosis.
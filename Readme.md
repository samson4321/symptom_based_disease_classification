Disease Prediction Using Machine Learning

(Symptom-Based Multi-Class Classification)

📌 Project Overview

This project investigates whether machine learning models can predict diseases using only:

Patient age

Patient gender

Self-reported symptoms

The task is formulated as a multi-class classification problem, where each patient is assigned one disease label from many possible diseases.

The project does not aim to build a real medical diagnostic system.
Instead, it focuses on understanding the limits of machine learning when the available data is insufficient.

📂 Dataset Description

Source: Kaggle Healthcare Dataset

Type: Structured tabular data

Target Variable: Disease (many disease classes)

Input Features

Age (continuous numerical feature)

Gender (categorical → one-hot encoded)

Symptoms (text field → converted into multiple binary symptom indicators)

Removed Columns

Patient_ID – identifier only, no predictive value

Symptom_Count – redundant after symptom encoding

🔄 Data Preprocessing Pipeline

The following preprocessing steps were applied carefully to ensure correctness and consistency:

1️⃣ Age Scaling

Age was scaled to the range [0, 1] using MinMaxScaler

This prevents age from dominating distance calculations in KNN

2️⃣ Gender Encoding

Gender was converted into:

Gender_Female

Gender_Male

Gender_Other

Boolean values were converted to 0/1

Gender features were not scaled

3️⃣ Symptom Encoding

The Symptoms text column (comma-separated symptoms) was:

Split into individual symptoms

Converted into binary (0/1) one-hot features

The original text column was removed

4️⃣ Train-Test Split

Dataset split into:

75% training

25% testing

Stratified split used to preserve disease distribution

🧠 Machine Learning Models Used
🔹 K-Nearest Neighbors (KNN)

Distance-based classifier

Tested with multiple values of k

Training vs test accuracy plotted to analyze overfitting

🔹 Random Forest Classifier

Ensemble-based model

Used as a baseline comparison

Helps confirm whether low accuracy is model-specific or data-related

📊 Evaluation & Visual Analysis
1️⃣ Class Distribution Analysis

Disease frequencies examined using:

Raw counts

Percentages

Visualization included:

Pie chart (for proportions)

Bar chart (for clarity with many classes)

📌 Result:
Classes are roughly balanced, so class imbalance is NOT the main problem.

2️⃣ Training vs Test Accuracy Curve (KNN)

A graph was generated showing:

Training accuracy vs number of neighbors (k)

Test accuracy vs number of neighbors (k)

Observed behavior:

k = 1 → training accuracy ≈ 100% (memorization)

Training accuracy decreases as k increases

Test accuracy remains very low for all k values

📌 Interpretation:

Small k → overfitting

Large k → underfitting

No value of k leads to good generalization

📈 Final Results
Model Accuracy Summary
Model	Accuracy
KNN (best k)	~3–4%
Random Forest	~3%
Classification Report

Precision, recall, and F1-score are very low across all diseases

No disease class is predicted reliably

Performance is close to random guessing

🧪 Interpretation of Results

The low accuracy is not caused by a bug, poor preprocessing, or incorrect model usage.

Instead, it reflects fundamental limitations of the dataset:

Key Reasons for Poor Performance

Large number of disease classes

Strong symptom overlap between diseases

Sparse, high-dimensional feature space

Lack of clinical depth

No lab tests

No severity indicators

No medical history

No temporal information

📌 Conclusion:

Symptoms alone are insufficient to reliably distinguish between many diseases.

❗ Important Insight

This project demonstrates an important machine learning principle:

Low accuracy does not always mean a bad model — it can mean insufficient information.

Understanding why a model fails is just as important as achieving high accuracy.

🚀 Possible Improvements (Future Work)
Data Improvements

Group diseases into broader categories (e.g., respiratory, neurological)

Remove very rare symptoms

Add clinical features (lab results, vitals, severity)

Modeling Improvements

Hierarchical classification

Gradient boosting models

Feature selection or dimensionality reduction

Evaluation Improvements

Top-k accuracy (e.g., is the correct disease in the top 5 predictions?)

Confusion matrix analysis for systematic errors

⚠️ Disclaimer

This project is for educational and experimental purposes only.
It must not be used for real medical diagnosis or clinical decision-making.

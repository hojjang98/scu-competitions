# 🧬 Thyroid Disease Prediction – SCU AI Challenge 2024

This project was developed as part of the **1st AI Modeling Competition** hosted by **Seoul Cyber University** in 2024.

The goal was to predict whether a patient shows signs of thyroid dysfunction  
using a combination of survey responses, medication history, and hormone test results.

> **Competition Link**: [SCU AI Competition 2024](https://www.kaggle.com/competitions/scu-ai-competition-202401)

---

## 🎯 Task Objective

The competition required building a classification model that predicts the presence of thyroid-related disease.

- **Type**: Binary Classification  
- **Target Variable**: `target`  
  - `1`: Indicates thyroid disease  
  - `0`: Indicates no thyroid disease

---

## 📂 Dataset Overview

The dataset includes a mix of categorical and numerical features related to health status.

### Example columns:

| Feature Name             | Description                      |
|--------------------------|----------------------------------|
| `나이`                   | Age                               |
| `성별`                   | Gender                            |
| `티록신_복용_여부`        | Whether the patient takes thyroxine |
| `갑상선저하_인지_여부`     | Whether the patient recognizes hypothyroidism |
| `TSH`, `FreeT3`, `FreeT4` | Hormone levels from blood tests   |
| `target`                 | Label indicating thyroid disease  |

> Note: Missing values exist in several columns (e.g., `TSH`, `FreeT3`), requiring preprocessing.

---

## ⚙️ Modeling Workflow

### 🔹 Step 1: Data Preprocessing
- Handled missing values using imputation strategies
- Converted categorical variables with one-hot encoding or label encoding

### 🔹 Step 2: Feature Engineering
- Preserved medically relevant variables like `TSH`, `FreeT3`, `FreeT4`
- Considered interactions between health status features and hormone levels

### 🔹 Step 3: Model Development
- Explored several classifiers:  
  - `RandomForestClassifier` (initial baseline)  
  - `LightGBMClassifier` (final model)

### 🔹 Step 4: Evaluation
- Cross-validation used for local testing  
- Final evaluation based on private Kaggle leaderboard

---

## 🧪 Results Summary

- **Final Model**: LightGBMClassifier  
- **Validation Metric**: F1 Macro  
- **Performance**: Showed robust results after feature tuning and handling imbalance

---

## 📁 Repository Structure

```bash
scu-2024-challenge/
├── data/
│   ├── train.csv
│   ├── test.csv
│   └── sample_submission.csv
├── notebooks/
│   └── scu_competition.ipynb
├── README.md
```

## 📄 Final Notebook

The complete, refactored notebook (with structured English comments and clean logic) is available here:

👉 [scu_2024_ai_competiton.ipynb](https://github.com/hojjang98/scu_ai_competitions/blob/main/scu-2024-challenge/notebooks/scu_2024_ai_competiton.ipynb)

---

## 🧠 Key Learnings

Even basic health indicators (e.g., 임신_여부, 지병_여부) provided valuable signal

Hormone levels required careful treatment due to missing and skewed values

LightGBM handled categorical + numerical mix efficiently

Feature simplicity outperformed overcomplicated transformations

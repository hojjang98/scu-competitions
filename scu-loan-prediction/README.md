# 🏦 Loan Grade & Diabetes Classification (SCU AI Competition – Excellence Award)

This project was developed for the **2nd AI Competition hosted by Seoul Cyber University**.  
The competition involved solving two classification problems:

- **Loan Grade Prediction** (multi-class classification)  
- **Diabetes Prediction** (binary classification)

---

## 🏆 Award  
**Excellence Award (우수상)**  
Awarded based on the **average performance across both tasks.**

### 🥇 Task 1: Loan Grade Prediction  
- [Leaderboard Link](https://www.kaggle.com/competitions/2-ai-loan/leaderboard)

### 🥈 Task 2: Diabetes Prediction  
- [Leaderboard Link](https://www.kaggle.com/competitions/2-ai/leaderboard)

---

## 🔍 Problem Overview

The competition involved two separate tabular classification problems:

1. **Loan grade classification** based on customer financial information  
2. **Diabetes classification** based on medical and demographic data

The core challenge was to apply effective **preprocessing and feature engineering** strategies  
to improve model performance in a **structured data** setting.

---

## 📦 Baseline Code Overview

A basic starter notebook was provided as a baseline, applying a `RandomForestClassifier`  
without significant preprocessing, feature engineering, or model tuning.

### 🔹 Baseline included:
- Dropping ID and label columns  
- Simple `train_test_split` (no cross-validation)  
- No missing value treatment  
- No engineered features  
- No hyperparameter tuning  
- Single model: `RandomForestClassifier`

While it served as a useful starting point, performance was limited by its simplicity.

📄 [Baseline Notebook: 고객대출등급 완전 베이스.ipynb](./고객대출등급 완전 베이스.ipynb)

---

## 🧪 Experiment Timeline Summary

Through 40+ submissions, I conducted extensive experimentation in iterative phases.

### 🔹 Phase 1: Establishing a Baseline (Submissions #1–#3)
- Basic preprocessing (mean/median imputation)
- Initial attempts at feature creation  
- Minor performance gains observed

---

### 🔹 Phase 2: Feature Engineering & Selection (Submissions #4–#12)
- Introduced domain-informed features such as:  
  - `이자부담율` (interest burden ratio)  
  - `근로기간 대비 신용거래기간 비율` (ratio of employment period to credit history length)  
- Applied scaling and encoding strategies  
- 🔥 Best single-feature result achieved using `이자부담율` (`0.6935`)

---

### 🔹 Phase 3: Model Exploration & Tuning (Submissions #6–#13)
- Compared multiple models: LightGBM, CatBoost, RandomForest, SVM  
- Eliminated underperformers  
- Tuned LightGBM and introduced ensemble methods  
- ✅ Best score in submission #13 using **LightGBM + Ensemble**

---

### 🔹 Phase 4: Feature Selection Refinement (Submissions #21–#30)
- Applied feature importance-based selection  
- Introduced ensemble voting/stacking with selected features  
- Used regularization to reduce overfitting

---

### 🔹 Phase 5: Post-peak Optimization (Submissions #31–#47)
- Tested feature interaction and reordering strategies  
- Conducted Optuna-based hyperparameter tuning  
- Some regressions observed — highlighting the importance of simplicity

Throughout, I emphasized **hypothesis-driven testing**, **reproducibility**, and **failure analysis**.

---

### 🧠 Task 2: Diabetes Classification

The second task involved predicting diabetes status using structured medical and demographic features.  
This dataset included missing values and **class imbalance**, which required careful handling.

📁 [Baseline Notebook (to be added)](./당뇨병 예측 이진분류(베이스라인 코드).ipynb)

---

## 🧪 Experiment Timeline Summary (Task 2)

Total of 40+ submissions, key stages:

### 🔹 Phase 1: Data Cleaning & Feature Addition (#1–#6)
- Handled missing values using domain logic  
  (e.g., gender-based imputation, mode value replacement)  
- Added custom features based on medical understanding  
  (e.g., derived variables from hemoglobin A1c)  
- ✅ Best improvement came from manual feature addition

---

### 🔹 Phase 2: Model Comparison (#7–#13)
- Evaluated LightGBM, CatBoost, RandomForest  
- LightGBM showed best results even with minimal tuning

---

### 🔹 Phase 3: Feature Engineering & Interaction (#14–#20)
- Introduced feature interactions such as:  
  - `[BMI × 혈당]`, `[나이 × 당화혈색소]`  
- Submission #18 yielded highest score: **0.811983** on Kaggle

---

### 🔹 Phase 4: Ensemble & Tuning (#21–#40)
- Applied:
  - Voting & Stacking  
  - Class weight balancing  
  - SMOTE for oversampling  
  - Optuna for hyperparameter search  
- F1 Macro peaked at **0.894** (validation), with Kaggle best at **0.811983**

---

## 🤖 Models Used

| Model          | Used | Notes                              |
|----------------|------|------------------------------------|
| LightGBM       | ✅    | Best performer; highly tunable    |
| CatBoost       | ✅    | Stable results; used selectively  |
| XGBoost        | ✅    | Strong in final tuning stages     |
| RandomForest   | ✅    | Baseline only                     |
| SVM            | ❌    | Low performance; discarded        |

---

## 💡 Key Learnings

- Simple engineered features like `[당화혈색소, 혈당차이]` were highly predictive  
- Excessively complex pipelines sometimes degraded generalization  
- LightGBM + Feature Selection + Optuna formed the best-performing combo  
- Pseudo-labeling and SMOTE were only effective under certain conditions

> 📌 This project taught me how **feature design, model selection, and ensemble strategies**  
> interact to shape the final performance in real-world tabular ML tasks.

# 🏦 Loan Grade & Diabetes Classification (SCU AI Competition – Excellence Award)

This project was developed for the 2nd AI Competition hosted by Seoul Cyber University.  
The goal was to predict:
- **Loan Grade (multi-class classification)**
- **Diabetes Status (binary classification)**

---

## 🏆 Award
- **Excellence Award (우수상)**  
  Awarded based on combined performance in two tasks:

### 🥇 Task 1: Loan Grade Prediction (Multi-class Classification)
- [Leaderboard Link](https://www.kaggle.com/competitions/2-ai-loan/leaderboard)

### 🥈 Task 2: Diabetes Prediction (Binary Classification)
- [Leaderboard Link](https://www.kaggle.com/competitions/2-ai/leaderboard)

> 🧮 Final score was based on the average performance across both tasks.

---

## 🔍 Problem Overview

Two tasks were involved:
1. **Loan grade prediction** using customer financial data
2. **Diabetes classification** using medical information

The main challenge was designing effective preprocessing and feature engineering strategies  
to improve model performance on tabular data.

---

## 📦 Baseline Code Overview

The competition provided a basic starter notebook as a baseline.  
It used minimal preprocessing and applied a `RandomForestClassifier` to the loan grade prediction task.

### 📄 What the baseline did:
- Dropped ID and label columns
- Applied simple `train_test_split` (no cross-validation)
- No missing value treatment
- No feature engineering
- No model tuning
- Used only `RandomForestClassifier`

This baseline achieved a reasonable initial score but left much room for improvement.

### 🚩 My Takeaways
- The baseline was helpful for understanding the structure of the data
- But the lack of preprocessing and feature engineering limited its performance
- It served as a foundation for iterative experimentation and model improvement
📄 [Baseline Notebook: 고객대출등급 완전 베이스.ipynb](./고객대출등급 완전 베이스.ipynb)

---

---

## 🧪 Experiment Timeline Summary

Over 40+ submissions, I iteratively refined the model through:

### 🔹 Phase 1: Establishing a Baseline (Submissions #1–#3)
- Minimal preprocessing
- Early imputation methods (mean, median)
- Initial feature engineering attempts
- 📈 Small score improvements

---

### 🔹 Phase 2: Feature Engineering & Selection (Submissions #4–#12)
- Created domain-specific features:
  - 이자부담율 (interest burden ratio)
  - 근로기간 대비 신용거래기간 비율
- Tried scaling & encoding strategies
- 🔥 Best single-feature performance from 이자부담율 alone (`0.6935`)

---

### 🔹 Phase 3: Model Exploration & Tuning (Submissions #6–#13)
- Compared LightGBM, CatBoost, RandomForest, SVM
- Rejected underperformers (e.g., RandomForest)
- Tuned LightGBM & applied ensemble
- ✅ Best score achieved with **LightGBM + Ensemble** in submission #13

---

### 🔹 Phase 4: Advanced Feature Selection (Submissions #21–#30)
- Feature importance-based selection
- Voting/stacking ensemble with top N features
- Applied regularization to reduce overfitting

---

### 🔹 Phase 5: Post-peak Optimization (Submissions #31–#47)
- Experiments with feature reordering, interaction variables
- Explored Optuna tuning & model combinations
- Some regressions observed, validating importance of simplicity

---

📌 Throughout the process, I emphasized reproducibility, hypothesis-driven testing, and failure analysis.  
This hands-on experimentation led to a deeper understanding of model behavior and performance tradeoffs.

---

## 🧠 Task 2: Diabetes Prediction (Binary Classification)

This task involved predicting whether an individual was diabetic based on medical and demographic features.  
The dataset had both missing values and imbalanced classes, making preprocessing and model choice crucial.

### 📄 Baseline Overview
The baseline model used a simple RandomForestClassifier without tuning or advanced preprocessing.

📁 [Baseline Notebook (to be added)](./당뇨병 예측 이진분류(베이스라인 코드).ipynb)

---

## 🧪 Experiment Timeline Summary

Total of 40+ submissions, key phases:

### 🔹 Phase 1: Data Cleaning & Feature Addition (#1–#6)
- Handled missing values using domain logic (e.g., 최빈값, 성별 → 여성)
- Added derived features: 당화혈색소 관련 파생 변수
- ✅ Best improvement from manually added features

### 🔹 Phase 2: Model Exploration (#7–#13)
- Tried LightGBM, CatBoost, RandomForest
- LightGBM yielded best scores with minimal tuning

### 🔹 Phase 3: Feature Engineering & Selection (#14–#20)
- Interaction variables (ex: [BMI × 혈당], [나이 × 당화혈색소])
- Best result at **Submission #18**, Kaggle: **0.811983**

### 🔹 Phase 4: Ensemble & Tuning (#21–#40)
- Applied:
  - Stacking, Voting
  - Class weights
  - SMOTE
  - Optuna-based tuning
- F1 Macro Score peaked at **0.894** on validation, Kaggle best: **0.811983**

---

## 🤖 Models Used

| Model | 사용 여부 | 비고 |
|-------|-----------|------|
| `LightGBM` | ✅ Best performer | 튜닝 및 앙상블에 가장 적합 |
| `CatBoost` | ✅ 안정적 성능 | 일부 실험에서 사용 |
| `XGBoost` | ✅ 최종 튜닝용 | 일부 특성 조합에서 성능 우수 |
| `RandomForest` | ✅ 베이스라인 | 초기 실험용 |
| `SVM` | ❌ Not effective | 실험했으나 성능 낮음 |

---

## 🧠 Key Learnings

- Simple feature combinations like [당화혈색소, 혈당차이] produced strong signals
- Overengineering sometimes degraded performance
- LightGBM + Optuna + Feature Selection = 최적의 조합
- Pseudo labeling 및 SMOTE는 주의가 필요함

> 📌 From feature engineering to ensemble strategy,  
> I learned the importance of balancing model complexity and generalizability.






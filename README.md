# AI-Driven Credit Card Fraud Detection
### Random Forest · XGBoost · Neural Network · SHAP Explainability

> **End-to-end machine learning project detecting credit card fraud across 568,630 real-world transactions — achieving 100% recall and 99.99% accuracy with full model explainability.**

---

## 📊 Results at a Glance

| Model | Accuracy | Precision | Recall | F1 Score | AUC |
|---|---|---|---|---|---|
| **Random Forest** | **99.99%** | **99.97%** | **100.000%** | **99.99%** | **1.0000** |
| Neural Network | 99.95% | 99.89% | 100.000% | 99.95% | 1.0000 |
| XGBoost | 99.77% | 99.71% | 99.842% | 99.77% | 0.9999 |

**Random Forest is the recommended production model** — perfect recall means zero fraudulent transactions missed across 113,726 test cases.

---

## 🏦 Business Problem

Financial fraud is one of the fastest-growing threats to the Australian financial system. According to ASIC (2023), between July 2021 and June 2022, more than **31,700 customers** of the four major Australian banks lost over **AUD $558 million** through scams — a **50% increase** in financial losses year on year.

**Core question:** How can financial institutions implement real-time fraud detection with high accuracy while ensuring seamless customer experiences and minimising false positives?

**Three specific challenges addressed:**
1. Accurately detecting fraudulent transactions in real time without disrupting legitimate activity
2. Minimising false positives — incorrectly blocking legitimate transactions damages customer trust
3. Building models that are explainable and auditable for regulatory compliance

---

## 📁 Project Structure

```
ai-fraud-detection-ml/
├── AI_Fraud_Detection_Portfolio.ipynb   ← Main analysis notebook
└── README.md
```

---

## 🔬 Methodology

### Dataset
- **Source:** Credit Card Fraud Detection Dataset 2023 — Kaggle (Nelgiriyewithana, 2023)
- **Size:** 568,630 anonymised credit card transactions from European cardholders
- **Features:** 28 PCA components (V1–V28) + Amount + Class
- **Class balance:** ~50/50 fraud vs non-fraud (balanced dataset)

### Notebook Structure

| Section | Content |
|---|---|
| 1. Setup & Data Loading | Libraries, dataset download via kagglehub |
| 2. Exploratory Data Analysis | Class distribution, amount analysis, correlation heatmap, PCA scatter |
| 3. Feature Engineering | Log_Amount transform, High_Value_Transaction flag |
| 4. Preprocessing | Train/test split (80/20), StandardScaler |
| 5. Random Forest | Training, evaluation, feature importance, ROC curve |
| 6. XGBoost | Training, evaluation, confusion matrix |
| 7. Neural Network | Keras Sequential model with BatchNorm and Dropout |
| 8. Model Comparison | Side-by-side metrics, ROC overlay, bar chart comparison |
| 9. SHAP Explainability | Feature importance bar, beeswarm, waterfall plots |
| 10. Business Impact | Financial translation of results + 3 recommendations |

---

## 💡 Key Findings

### Model Performance
- **Random Forest and Neural Network both achieve 100% recall** — zero fraud missed
- **XGBoost recall drops to 99.842%** — in fraud detection, every missed fraud is a real customer loss
- All 3 models achieve ROC AUC ≥ 0.9999 — near-perfect separation of fraud from legitimate transactions

### SHAP Explainability
| Rank | Feature | SHAP Contribution | Impact |
|---|---|---|---|
| 1 | V14 | +0.14 | Strongest fraud signal |
| 2 | V12 | +0.08 | Second strongest predictor |
| 3 | V17 | +0.08 | Consistently elevated in fraud |
| 4 | V10 | +0.07 | Fourth most influential |
| 5 | V4 | +0.06 | Complex bidirectional pattern |

SHAP waterfall plots provide **transaction-level explanations** — every fraud flag is fully auditable and defensible to compliance teams and regulators.

### Business Impact (Random Forest — Test Set)
| Metric | Result |
|---|---|
| Fraud detection rate | **100%** — zero fraudulent transactions missed |
| False positive rate | **0.032%** — only 18 legitimate transactions wrongly blocked |
| Estimated fraud value protected | **AUD $8,529,450** |
| Estimated fraud value missed | **AUD $0** |

---

## 📈 Visualisations

The notebook produces 12 publication-quality charts:

- Class distribution (bar + pie)
- Transaction amount analysis by class
- Feature correlation heatmap
- PCA scatter — fraud clustering in 2D
- Random Forest confusion matrix
- XGBoost confusion matrix
- Neural Network confusion matrix
- ROC curve — all 3 models overlaid
- 3-model performance bar chart
- SHAP feature importance bar chart
- SHAP beeswarm plot
- SHAP waterfall — single transaction explanation

---

## 🏆 Comparison to Industry Benchmarks

| Detection System | Typical Recall |
|---|---|
| Rule-based systems | 70–85% |
| Standard ML models | 90–95% |
| **This Random Forest** | **100%** |

---

## 💼 Three Business Recommendations

**Rec 1 — Deploy Random Forest as primary real-time transaction screener**
The model achieves 100% recall and 99.99% accuracy across 568,630 transactions. Integrate via API into the transaction processing pipeline. Fraud probability >0.85 → auto-block. Probability 0.50–0.85 → analyst review queue.

**Rec 2 — Apply secondary human review for high-value transactions**
Transactions above the 95th percentile threshold carry elevated fraud risk. All High_Value_Transaction=1 cases should receive human review within 60 seconds regardless of model score.

**Rec 3 — Migrate to streaming architecture for real-time prevention**
Deploy via Apache Kafka + Spark MLlib for sub-100ms transaction scoring — blocking fraud before it completes rather than detecting it after. Recommended as a 6-month implementation target.

---

## 🛠️ Tools & Libraries

![Python](https://img.shields.io/badge/Python-3.10-blue?logo=python&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-ML-orange?logo=scikit-learn&logoColor=white)
![XGBoost](https://img.shields.io/badge/XGBoost-Gradient%20Boosting-red)
![TensorFlow](https://img.shields.io/badge/TensorFlow-Neural%20Network-FF6F00?logo=tensorflow&logoColor=white)
![SHAP](https://img.shields.io/badge/SHAP-Explainability-purple)
![Google Colab](https://img.shields.io/badge/Google%20Colab-Notebook-F9AB00?logo=googlecolab&logoColor=white)

| Library | Purpose |
|---|---|
| pandas, numpy | Data manipulation |
| matplotlib, seaborn | Visualisation |
| scikit-learn | Random Forest, preprocessing, metrics |
| XGBoost | Gradient boosting model |
| TensorFlow / Keras | Neural network |
| SHAP | Model explainability |
| kagglehub | Dataset download |

---

## 🚀 How to Run

1. Open [Google Colab](https://colab.research.google.com)
2. Upload `AI_Fraud_Detection_Portfolio.ipynb`
3. Run the first cell — it installs all dependencies automatically:
```python
!pip install xgboost kagglehub shap -q
```
4. Run all cells — the dataset downloads automatically via kagglehub
5. Total runtime: approximately 15–20 minutes (Random Forest training is the longest step)

---

## 📚 References

- ASIC (2023). *Scam prevention, detection and response by the four major banks — Report 761.*
- Aburbeian, A. & Ashqar, H. Credit Card Fraud Detection Using Enhanced Random Forest Classifier for Imbalanced Data. arXiv:2303.06514.
- Khalid et al. (2024). Enhancing Credit Card Fraud Detection: An Ensemble Machine Learning Approach. *Big Data and Cognitive Computing*, 8(1), p.6.
- Marazqah Btoush et al. (2023). A systematic review of literature on credit card cyber fraud detection. *PeerJ Computer Science*, 9, e1278.
- Nelgiriyewithana (2023). Credit Card Fraud Detection Dataset 2023. Kaggle.

---

## 👤 Author

**Stanley Okoye**
Masters of Business Analytics
Portfolio Project — April 2026

---

## 🤖 Development Note

This project was developed with analytical guidance and code review support from **Claude (Anthropic)** — an AI assistant used to structure the analysis, debug code, and translate model results into business recommendations. All domain decisions, model selection rationale, and business framing reflect the author's own judgement informed by prior academic work in fraud detection analytics.

---

## 📌 Related Portfolio Projects

- [RetailCo Returns Process — BA Portfolio Project](https://github.com/stanokoye/retailco-returns-process-analysis)
- [TSPH Hospital Referral Optimisation — BA Portfolio Project](https://github.com/stanokoye/tsph-referral-optimisation)

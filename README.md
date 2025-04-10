# myeloid-survival-prediction
QRT 2025 Challenge: Predicting Overall Survival for Patients with Myeloid Leukemia

# 🧬 Overall Survival Prediction for Myeloid Leukemia (QRT Challenge)

This repository contains my solution for the [QRT Data Science Challenge](https://challengedata.ens.fr/challenges/112), focused on predicting overall survival for patients diagnosed with myeloid leukemia. The task involves using tabular clinical and molecular data to predict risk scores that reflect a patient's likelihood of death, allowing for more personalized and timely treatment strategies.

---

## 🧠 Project Goals

- Predict a continuous **risk score** for mortality using patient-level data.
- Handle **right-censored survival data** via appropriate models and evaluation metrics.
- Apply and compare various modeling approaches:
  - Cox Proportional Hazards Model (semi-parametric)
  - Gradient-boosted trees (LightGBM / XGBoost)
  - Deep tabular models (e.g., TabNet)
- Perform meaningful **feature engineering** using both:
  - Clinical indicators (e.g., blood counts, cytogenetics)
  - Genetic mutations (molecular-level data)

---

## 🗂️ Repository Structure

```
leukemia-survival-prediction/
├── data/               # Local-only; contains X_train, X_test, Y_train.csv
├── notebooks/          # EDA, preprocessing, and modeling workflows
│   ├── 01_eda.ipynb
│   ├── 02_preprocessing.ipynb
│   └── 03_modeling.ipynb
├── src/                # Modular pipeline code
│   ├── data_loader.py
│   ├── feature_engineering.py
│   └── models/
│       ├── cox.py
│       ├── xgboost_model.py
│       └── tabnet_model.py
├── outputs/            # Model predictions, saved weights, visualizations
├── requirements.txt    # Python dependencies
└── README.md           # Project overview and instructions
```


---

## 📁 Data Access

> ⚠️ **Important**: Due to licensing terms, the datasets are **not publicly available** in this repository.

To reproduce the results:
1. Register and download the files from the official [ChallengeData QRT page](https://challengedata.ens.fr/challenges/112).
2. Extract the files into a local `data/` directory with the following structure:
```
├── data/                 
│   ├── X_train/          # Clinical and molecular training data (unzipped)
│   ├── X_test/           # Clinical and molecular test data (unzipped)
│   └── Y_train.csv       # Survival times and status for training
```


---

## 📈 Evaluation Metric

The challenge uses the **IPCW-Concordance Index (C-index)** for right-censored data. This metric:
- Compares pairwise survival ranking predictions.
- Weighs censored samples using inverse probability methods.
- Evaluates **ranking accuracy** of risk scores, not absolute time prediction.

A higher C-index (closer to 1) indicates better performance.

---

## 📊 Models Explored

- ✅ Cox Proportional Hazards (baseline)
- ✅ LightGBM and XGBoost (non-censoring-aware)
- 🧪 Deep learning: TabNet (interpretable attention-based architecture)
- 🧬 Molecular data parsing + aggregation
- 🔧 Categorical feature encoding (e.g., cytogenetics, gene mutation effects)

---

## 🚀 Getting Started

Install required packages:
```bash
pip install -r requirements.txt
```

Run the notebooks in order:

    01_eda.ipynb – Exploratory Data Analysis

    02_preprocessing.ipynb – Merging & cleaning

    03_modeling.ipynb – Model training & evaluation

📜 License & Data Use

This repository is for educational and research purposes only.
Do not redistribute the original data files — they are property of Qube Research & Technologies and Institut Gustave Roussy.

📬 Contact

For questions, suggestions, or collaboration: [@ely2ba]
Feel free to open an issue or discussion.


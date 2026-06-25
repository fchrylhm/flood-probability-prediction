# 🌊 Flood Probability Prediction — Data Science Competition (Preliminary Round)

> **Team:** es_kelapa_lovers  
> **Institution:** Universitas Singaperbangsa Karawang (UNSIKA)  
> **Competition:** Data Science Preliminary Round  
> **Task:** Regression & Clustering — Predicting Flood Probability from Environmental Risk Factors

---

## 📌 Project Overview

This project was submitted as part of a **Data Science Competition Preliminary Round**. The goal is to predict the probability of flooding (`FloodProbability`) based on 20 environmental and infrastructural risk features, using a combination of regression models and unsupervised clustering.

The notebook covers the full data science pipeline:
- Exploratory Data Analysis (EDA)
- Feature Engineering (Total Risk Index / TRI)
- Model Training & Evaluation (Linear Regression, Random Forest, XGBoost)
- K-Means Clustering with PCA visualization
- Visual Risk Intelligence Dashboard

---

## 📂 Repository Structure

```
├── Notebook_Preliminary_es_kelapa_lovers.ipynb   # Main analysis notebook
├── requirements.txt                               # Python dependencies
├── .gitignore                                     # Files excluded from version control
└── README.md                                      # Project documentation (this file)
```

> **Note:** The dataset file `flood.csv` is not included in this repository as it is provided by the competition organizer.

---

## 🧠 Methodology

### 1. Data Loading & Validation
- Dataset loaded from `flood.csv`
- All 20 features confirmed to be within the valid range `[0, 10]`
- No outliers detected — distribution is approximately symmetric

### 2. Feature Engineering
- **Total Risk Index (TRI):** Engineered feature computed as the sum of all 20 risk factors per record
- TRI threshold bands defined: Low (< 70), Moderate (70–110), High (110–150), Critical (> 150)

### 3. Exploratory Data Analysis
| Figure | Description |
|--------|-------------|
| Fig. 1 | Correlation Heatmap — 20 Features vs. FloodProbability |
| Fig. 2 | Distribution of FloodProbability |
| Fig. 3 | TRI Distribution with Visual Risk Threshold Bands |

### 4. Model Training
Stratified train/test split (80/20) was used, stratified by `RiskCategory` (Low / Moderate / High / Critical).

| Model | Type |
|-------|------|
| Linear Regression (OLS) | Baseline regression |
| Random Forest Regressor | Ensemble (n=100 trees) |
| XGBoost Regressor | Gradient boosting |

### 5. Evaluation & Insight Extraction
| Figure | Description |
|--------|-------------|
| Fig. 4 | Predicted vs. Actual FloodProbability (all 3 models) |
| Fig. 7 | OLS β Coefficient Analysis |
| Fig. 8 | Top 5 Dominant Features (XGBoost & Random Forest) |
| Fig. 9 | Full Feature Importance Ranking — All 20 Attributes |

### 6. Unsupervised Clustering
- K-Means clustering with k=3 (Elbow Method used to validate)
- Clusters labeled based on TRI centroid: **Aman** (Safe), **Waspada** (Caution), **Bahaya** (Danger)
- PCA used to project clusters into 2D for visualization

| Figure | Description |
|--------|-------------|
| Fig. 6 | K-Means Clustering (k=3) — 2D PCA Projection |
| Fig. 10 | Visual Risk Intelligence Dashboard |

---

## 🛠️ Tech Stack

| Category | Libraries |
|----------|-----------|
| Data Manipulation | `pandas`, `numpy` |
| Visualization | `matplotlib`, `seaborn` |
| Machine Learning | `scikit-learn` |
| Gradient Boosting | `xgboost` |

---

## ⚙️ Setup & Usage

### 1. Clone the Repository
```bash
git clone https://github.com/<your-username>/<repo-name>.git
cd <repo-name>
```

### 2. Create a Virtual Environment (Recommended)
```bash
python -m venv venv
source venv/bin/activate        # Linux/macOS
venv\Scripts\activate           # Windows
```

### 3. Install Dependencies
```bash
pip install -r requirements.txt
```

### 4. Add the Dataset
Place the `flood.csv` file (provided by the competition organizer) into the root of the project directory.

### 5. Run the Notebook
```bash
jupyter notebook Notebook_Preliminary_es_kelapa_lovers.ipynb
```

---

## 📊 Key Findings

- **XGBoost** achieved the highest R² score among the three models, confirming its suitability for this regression task.
- All 20 features contribute roughly equally to flood probability, reflecting the dataset's symmetric design — consistent with the near-uniform OLS β coefficients (~1/200 each).
- K-Means clustering successfully segmented the data into three interpretable risk zones, validated by TRI centroid values.
- The **Visual Risk Intelligence Dashboard** (Fig. 10) shows strong alignment between XGBoost predictions and actual risk category distributions.

---

## 👥 Team

| Name | Role |
|------|------|
| *(Team es_kelapa_lovers)* | Data Analysis, Feature Engineering, Modeling |

> *Universitas Singaperbangsa Karawang (UNSIKA)*

---

## 📄 License

This project is submitted for academic competition purposes. Dataset rights belong to the competition organizer.

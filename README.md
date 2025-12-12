# Machine Learning Analysis of Income Determinants in Mexico (2000–2020)

This repository contains an applied machine learning project analyzing the determinants of labor income in Mexico between 2000 and 2020, with a focus on how the predictive role of education has evolved over time. Using harmonized census microdata, the project compares linear and non-linear models and applies modern interpretability tools to study income inequality in a data-driven way.

The objective is **predictive and descriptive**, not causal.

---

## Project Goal

**Assess whether education has become more important in predicting income over time, relative to other individual and labor-market characteristics.**

---

## Data

- **Source:** Harmonized Mexican census microdata (Banco de México)  
- **Years:** 2000, 2010, 2015, 2020  
- **Unit of observation:** Individual  
- **Sample:** 15,996 individuals (random sample, age ≥ 18, positive income)  
- **Target variable:** Monthly labor income (log-transformed)

**Key features**
- Years of education
- Age, gender
- Ethnic identification
- Marital status and religion (grouped)
- Occupation and commute time
- Local labor market identifier

---

## Methods

- **Models:** Linear Regression, Ridge, Lasso, Random Forest, Gradient Boosting  
- **Evaluation:** 5-fold cross-validation; test-set MSE, MAE, R²  
- **Feature engineering:**
  - Education × year interaction
  - One-hot encoding for low-cardinality variables
  - Target encoding for high-cardinality local labor markets
  - Standardization of numerical features
- **Interpretability:** SHAP values for consistent comparison across models

---

## Key Findings

- Gradient Boosting achieves the best predictive performance (R² ≈ 0.40), followed closely by linear and ridge regression.
- Education is consistently an important predictor, but its **relative importance and interaction with time differ across model classes**.
- Non-linear models emphasize structural labor-market conditions, while linear models highlight education more directly.
- Results suggest income inequality reflects a combination of **individual human capital** and **local labor-market structure**, interacting over time.

---

## Repository Structure

├── README.md
├── LICENSE
│
├── cleandata/
│   └── combined_personas_sample.csv     # Final analytical dataset
│
├── code/
│   ├── 00_sample_cleaning.ipynb          # Sampling and initial filtering
│   ├── 01_cleaning.ipynb                 # Data cleaning and feature engineering
│   └── 02_exploration_and_models.ipynb   # EDA, modeling, SHAP analysis
│
├── output/
│   ├── figures/                          # Plots and visualizations
│   │   ├── income_by_education_year.png
│   │   ├── demographic_distributions*.png
│   │   ├── correlation_matrix.png
│   │   ├── gbr_shap_beeswarm.png
│   │   └── lr_shap_beeswarm.png
│   │
│   ├── tables/                           # Model results (LaTeX-ready)
│   │   ├── model_performance_comparison.tex
│   │   └── models_top_variables.tex
│   │
│   └── 02_exploration_and_models.html    # Rendered notebook
│
├── admin/
│   ├── Income_Determinants_Mexico_report.pdf
│   └── IncomeDeterminantsMexico_ppt.pdf
│
└── lit_review/
    └── references/                       # Background literature (ML, education, income)

---

## Scope & Limitations

- Predictive analysis only (no causal interpretation)
- Income may be underreported due to informality
- Education measured as years of schooling (no quality dimension)
- Target encoding may absorb regional structure


 

# Assignment 2 – Predicting Fast-Growing Firms

This folder contains all materials for **Data Analysis 3 – Assignment 2**, which focuses on predicting the probability that a firm is fast-growing using Bisnode firm-level data.

The assignment consists of:
- A full data preparation pipeline
- Probability prediction models (Logit, LASSO, Random Forest)
- Cost-sensitive classification using an asymmetric loss function
- A manager-style summary report and a technical report

---

## Folder Structure

```

assignment_2/
├── data/
│   └── bisnode_firms_clean_50%.csv
│
├── notebooks/
│   ├── assignment_2_final.ipynb
│   ├── ch17-firm-exit-data-prep.ipynb
│   └── py_helper_functions.py
│
├── reports/
│   ├── DA3_Assignment_2_report.pdf
│   └── DA3_Assignment_2_technical_report.pdf
│
└── README.md

```

---

## Data

- `data/bisnode_firms_clean_50%.csv`  
  Cleaned firm-level dataset derived from the original Bisnode panel (2010–2015).  
  Contains financial variables, firm characteristics, management variables, and data quality flags, as well as the constructed target variable `fast_growth`.

---

## Notebooks

- `notebooks/ch17-firm-exit-data-prep.ipynb`  
  Data preparation notebook.  
  Starts from the raw panel and produces the cleaned dataset used in the analysis. This notebook is taken from the class materials, and only a few cells are modified to achieve the goal of this assignment. Whatever is modified is marked as modified.

- `notebooks/assignment_2_final.ipynb`  
  Main analysis notebook.  
  Contains:
  - Train / holdout split
  - Feature engineering and model specifications (M1–M5, LASSO, Random Forest)
  - 5-fold cross-validation
  - Evaluation using Brier RMSE and AUC
  - Cost-sensitive classification with asymmetric loss (FN = 10, FP = 1)
  - Threshold optimization
  - Holdout evaluation
  - Industry-specific analysis (Manufacturing vs Services)

- `notebooks/py_helper_functions.py`  
  Helper functions taken from the class materials.

---

## Reports

- `reports/DA3_Assignment_2_report.pdf`  
  **Manager summary report** (non-technical audience):  
  Focuses on:
  - Business problem
  - Model comparison
  - Decision rule based on asymmetric loss
  - Final recommendation
  - Industry comparison

- `reports/DA3_Assignment_2_technical_report.pdf`  
  **Technical report**:  
  Documents:
  - Data construction
  - Feature engineering
  - Model choices
  - Cross-validation setup
  - Evaluation metrics
  - Threshold optimization
  - Holdout results
  - Industry-specific analysis
  - Methodological decisions

---

## How to Reproduce the Results

1. Open `notebooks/ch17-firm-exit-data-prep.ipynb` (optional, if starting from raw data). Disclaimer: because of the file size of the original csv, I could not display it in the repo. To achieve the new dataset please add the original csv to your local machine.
2. Open and run `notebooks/assignment_2_final.ipynb`
3. Make sure the path to `data/bisnode_firms_clean_50%.csv` is correct
4. Run all cells to reproduce:
   - Cross-validation results
   - Plots (ROC, loss curves, calibration where applicable)
   - Tables used in the reports

---

## Modeling Summary

- Models estimated:
  - Logistic Regression (M1–M5)
  - LASSO Logistic Regression
  - Random Forest
- Evaluation metrics:
  - Brier RMSE (probability accuracy)
  - AUC (ranking performance)
  - Expected Loss with asymmetric costs (FN = 10, FP = 1)
- Final model choice:
  - **Random Forest**, due to lowest cross-validated expected loss
- Additional analysis:
  - Separate evaluation for Manufacturing and Services firms

---

## Authors

- Elene Zuroshvili  
- Luciana Solari Razuri  

---

## Notes

- The focus of this assignment is **probability prediction and cost-sensitive classification**, not just accuracy.
- Thresholds are chosen by minimizing expected loss, not by using the default 0.5 cutoff.
- The reports in `reports/` are the final submission documents.

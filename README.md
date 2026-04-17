# Breast Cancer Survival Analysis

Comparison of machine learning survival models for breast cancer prognosis using nested cross-validation, with SHAP-based explainability for the best-performing model.

## Models

- Penalized Cox Proportional Hazards (`glmnet`)
- Random Survival Forest (`aorsf`)
- Gradient Boosted Survival Trees (`mboost`)
- Survival Decision Tree (`rpart`)

## Methods

All models were tuned and evaluated using a 5×5 nested cross-validation framework via `tidymodels` and `censored`. Hyperparameters were selected by maximising the concordance index (C-index) on the inner folds, with final performance assessed on the outer folds using the C-index, time-dependent AUC, and integrated Brier score. Final models were fit on the full dataset using the median hyperparameters across outer folds. The best-performing model was explained using SurvSHAP(t) values via `survex`.

## Requirements

R ≥ 4.2.0 and the following packages:

```r
install.packages(c(
  "tidyverse", "tidymodels", "censored", "aorsf",
  "mboost", "glmnet", "survex", "future", "furrr"
))
```

## Usage

1. Place `Breast Cancer Kiki1.csv` in the project root directory.
2. Open and run `survival_analysis.R` sequentially.

## Data

The dataset contains breast cancer patient records with event time and event indicator as the survival outcome. Due to patient privacy, the raw data is not included in this repository.

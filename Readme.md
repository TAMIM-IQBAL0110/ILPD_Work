# ILPD_Work

Code, executed notebook and results for the manuscript:

**Logistic Regression versus Ensemble Learners and SHAP Explanation Stability in a Small Referral Cohort: A Nested-Validation Audit of the Indian Liver Patient Dataset**

## Overview

This repository reproduces every table and figure in the manuscript. The study re-analyses the Indian Liver Patient Dataset (ILPD) with a leakage-free, repeated nested cross-validation design and asks what a rigorously validated analysis of one small clinical cohort can conclude. It covers:

- Comparison of seven learners (logistic regression, random forest, ExtraTrees, XGBoost, LightGBM, CatBoost, RBF-SVM) with corrected confidence intervals and equivalence tests (TOST).
- Sensitivity to class-imbalance handling (SMOTE-NC, class weights) and a leakage replication.
- Calibration, decision-curve analysis, clinical baselines and subgroup performance.
- SHAP explanations: faithfulness against competing rankings (median replacement and retrain-without-feature) and a stability audit with a label-permuted null and a logistic-regression benchmark.
- Generalisation checks on five public datasets and a simulation with known ground truth.

The study follows the TRIPOD+AI reporting guideline. A section-by-section map is included in the notebook.

## Data

All data are public. No patient-level data were collected for this study.

| Dataset | Source |
|---|---|
| Indian Liver Patient Dataset (ILPD, 583 records; 566 after removing 4 incomplete records and 13 exact duplicates) | UCI Machine Learning Repository |
| Pima diabetes, SAheart, Cleveland heart disease, BUPA liver disorders, Haberman survival | Penn Machine Learning Benchmarks (PMLB) |

Download the datasets from the sources above if they are not already in this repository. File names and the positive-class coding for each dataset are listed in the notebook.

## Requirements

Versions used in the manuscript:

- Python 3.13
- scikit-learn 1.9.1
- imbalanced-learn 0.14.2
- XGBoost 3.4.1
- LightGBM 4.7.0
- CatBoost 1.2.10
- SHAP 0.54.1

Other common packages (NumPy, pandas, SciPy, statsmodels, matplotlib, InterpretML, Jupyter) are also needed. The global random seed is 42.

Install the main packages with:

```bash
pip install scikit-learn==1.9.1 imbalanced-learn==0.14.2 xgboost==3.4.1 \
    lightgbm==4.7.0 catboost==1.2.10 shap==0.54.1 \
    numpy pandas scipy statsmodels matplotlib interpret jupyter
```

## How to reproduce

1. Clone the repository and install the requirements.
2. Place the datasets where the notebook expects them (see the data section of the notebook).
3. Open the notebook in Jupyter and run all cells from top to bottom.

Results are cached, so after a first full run the notebook regenerates every table and figure quickly. A full run of the nested cross-validation, stability and simulation analyses is computationally heavy and may take several hours.

## Repository contents

- The executed Jupyter notebook, with source code, random seeds, analytical results, tables and figures.
- Supplementary Figures S1–S10 and Supplementary Tables S1–S6 referred to in the manuscript.

## Notes and limitations

- ILPD is a single-source, retrospective referral cohort with 71% prevalence. Calibrated probabilities, thresholds and net benefit do not transport to screening populations.
- The analyses were not pre-registered. Subgroup analyses are exploratory.
- An AI assistant (Claude, Anthropic) was used to help write analysis code and edit text. The authors re-ran the notebook and checked the reported results.

## Citation

If you use this code, please cite the manuscript above. Full citation details will be added after publication.

## Licence

Add a licence file (for example MIT) before publication so others can reuse the code.

## Contact

Questions and issues: please open an issue on this repository.
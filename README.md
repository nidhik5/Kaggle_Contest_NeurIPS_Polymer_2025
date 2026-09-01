# NeurIPS Open Polymer Prediction 2025
 
Kaggle competition solution predicting **five polymer properties directly from molecular SMILES structures**.
 
## Overview
 
Predict five polymer properties from polymer SMILES strings:
 
- **Tg** — glass transition temperature
- **FFV** — fractional free volume
- **Tc** — thermal conductivity
- **Density**
- **Rg** — radius of gyration
Submissions are scored on a **weighted Mean Absolute Error (wMAE)** across the five targets.
 
## Approach
 
- **Feature engineering (RDKit):** convert SMILES into molecular descriptors and Morgan fingerprints capturing physicochemical and structural properties.
- **Missing-label handling:** the targets are sparsely labeled (e.g., ~7.5k missing Tg, ~7.4k missing Density), so each property is trained on its available labels.
- **Multi-target modeling:** a multi-target regressor (one model per property) using an **ensemble of gradient-boosted trees (LightGBM, XGBoost, CatBoost) and bagged trees (RandomForest, ExtraTrees, GradientBoosting)**.
- **Evaluation:** a **custom Weighted-MAE scorer** matching the competition metric, validated with cross-validation.
## Results
 
- **Overall weighted MAE ≈ 0.031** (cross-validation).

| Property | MAE |
|----------|------|
| Tg       | 7.39 |
| FFV      | 0.017 |
| Tc       | 0.008 |
| Density  | 0.039 |
| Rg       | 1.52 |
 
## Repository
 
| File | Description |
|------|-------------|
| `polymer_prediction.ipynb` | Full pipeline: feature engineering, modeling, evaluation, submission |
| `train.csv`, `test.csv` | Competition data |
| `submission.csv`, `enhanced_submission.csv` | Generated predictions |
 
## Tech Stack
 
Python · pandas · NumPy · scikit-learn · LightGBM · XGBoost · CatBoost · RDKit
 
## Run
 
```bash
pip install pandas numpy scikit-learn lightgbm xgboost catboost rdkit-pypi
jupyter notebook polymer_prediction.ipynb
```

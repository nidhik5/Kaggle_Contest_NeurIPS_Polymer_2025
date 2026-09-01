# Kaggle_Contest_NeurIPS_Polymer_2025

NeurIPS Open Polymer Prediction 2025

Kaggle competition solution predicting five polymer properties directly from molecular SMILES structures.

Overview

Predict five polymer properties — glass transition temperature (Tg), fractional free volume (FFV), thermal conductivity (Tc), density, and radius of gyration (Rg) — from polymer SMILES strings. Scored on a weighted Mean Absolute Error (wMAE) across the five targets.

Approach
Feature engineering (RDKit): converted SMILES into molecular descriptors and Morgan fingerprints (physicochemical + structural features).
Missing-label handling: targets are sparsely labeled (e.g., ~7.5k missing Tg, ~7.4k missing Density), so each property is trained on its available labels.
Multi-target modeling: built a multi-target regressor (one model per property) with an ensemble of gradient-boosted trees (LightGBM, XGBoost, CatBoost) and bagged trees (RandomForest, ExtraTrees, GradientBoosting).
Evaluation: implemented a custom Weighted-MAE scorer matching the competition metric, validated with cross-validation.
Results
Overall weighted MAE ≈ 0.031 (cross-validation).
Per-property MAE — Tg: 7.39 · FFV: 0.017 · Tc: 0.008 · Density: 0.039 · Rg: 1.52.
Repository
polymer_prediction.ipynb — full pipeline: feature engineering, modeling, evaluation, submission.
train.csv, test.csv — competition data.
submission.csv, enhanced_submission.csv — generated predictions.
Tech Stack

Python · pandas · NumPy · scikit-learn · LightGBM · XGBoost · CatBoost · RDKit

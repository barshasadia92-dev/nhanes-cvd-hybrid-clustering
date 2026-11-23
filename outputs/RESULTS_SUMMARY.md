# Results Summary

_Generated automatically by the notebook. Test set: n = 1,172 (CVD prevalence 9.73%). Training set: n = 4,684._

## Clustering
- K = 3 (silhouette-optimal K on training data: 3).
- Mean silhouette over 20 seeds: **0.185** (no substantial cluster structure (clusters overlap heavily)).
- Mean pairwise ARI across seeds: **0.995** (min 0.989).

## Held-out test performance (all 12 models)
Thresholds were selected from training out-of-fold predictions (maximise F1 subject to recall >= 0.7).

| Classifier | Version | Threshold | Accuracy | Precision | Recall_Sensitivity | Specificity | F1_Score | AUROC | AUPRC | FN | FP |
|---|---|---|---|---|---|---|---|---|---|---|---|
| Logistic Regression | Baseline | 0.43 | 0.755 | 0.251 | 0.763 | 0.754 | 0.377 | 0.837 | 0.290 | 27 | 260 |
| Logistic Regression | Pure Hybrid | 0.45 | 0.771 | 0.259 | 0.728 | 0.776 | 0.382 | 0.840 | 0.294 | 31 | 237 |
| Logistic Regression | Augmented Hybrid | 0.46 | 0.776 | 0.263 | 0.719 | 0.783 | 0.385 | 0.840 | 0.294 | 32 | 230 |
| Random Forest | Baseline | 0.31 | 0.751 | 0.240 | 0.719 | 0.754 | 0.360 | 0.835 | 0.307 | 32 | 260 |
| Random Forest | Pure Hybrid | 0.32 | 0.756 | 0.243 | 0.711 | 0.761 | 0.362 | 0.835 | 0.312 | 33 | 253 |
| Random Forest | Augmented Hybrid | 0.33 | 0.753 | 0.237 | 0.693 | 0.759 | 0.353 | 0.832 | 0.304 | 35 | 255 |
| SVM | Baseline | 0.13 | 0.753 | 0.237 | 0.693 | 0.759 | 0.353 | 0.828 | 0.295 | 35 | 255 |
| SVM | Pure Hybrid | 0.12 | 0.757 | 0.252 | 0.763 | 0.756 | 0.379 | 0.834 | 0.309 | 27 | 258 |
| SVM | Augmented Hybrid | 0.12 | 0.755 | 0.251 | 0.763 | 0.754 | 0.377 | 0.836 | 0.305 | 27 | 260 |
| XGBoost | Baseline | 0.37 | 0.721 | 0.230 | 0.798 | 0.713 | 0.358 | 0.828 | 0.275 | 23 | 304 |
| XGBoost | Pure Hybrid | 0.39 | 0.733 | 0.232 | 0.754 | 0.731 | 0.355 | 0.827 | 0.289 | 28 | 285 |
| XGBoost | Augmented Hybrid | 0.41 | 0.733 | 0.230 | 0.746 | 0.732 | 0.352 | 0.825 | 0.300 | 29 | 284 |

## Pure Hybrid minus matched Baseline (paired bootstrap, 1000 resamples)
| Classifier | Metric | Mean | CI_Lower | CI_Upper | Verdict |
|---|---|---|---|---|---|
| Logistic Regression | AUROC | +0.0025 | -0.0018 | +0.0073 | no clear difference |
| Logistic Regression | AUPRC | +0.0045 | -0.0052 | +0.0164 | no clear difference |
| Logistic Regression | F1 | +0.0049 | -0.0122 | +0.0205 | no clear difference |
| Logistic Regression | Recall | -0.0355 | -0.0734 | -0.0082 | decline |
| Random Forest | AUROC | +0.0007 | -0.0047 | +0.0062 | no clear difference |
| Random Forest | AUPRC | +0.0044 | -0.0096 | +0.0193 | no clear difference |
| Random Forest | F1 | +0.0024 | -0.0158 | +0.0219 | no clear difference |
| Random Forest | Recall | -0.0078 | -0.0480 | +0.0351 | no clear difference |
| SVM | AUROC | +0.0056 | -0.0006 | +0.0121 | no clear difference |
| SVM | AUPRC | +0.0110 | -0.0151 | +0.0360 | no clear difference |
| SVM | F1 | +0.0257 | +0.0042 | +0.0499 | improvement |
| SVM | Recall | +0.0684 | +0.0192 | +0.1259 | improvement |
| XGBoost | AUROC | -0.0011 | -0.0130 | +0.0112 | no clear difference |
| XGBoost | AUPRC | +0.0131 | -0.0130 | +0.0420 | no clear difference |
| XGBoost | F1 | -0.0025 | -0.0279 | +0.0199 | no clear difference |
| XGBoost | Recall | -0.0430 | -0.1072 | +0.0109 | no clear difference |

## Interpretation
- Primary model (selected by training OOF F1, not by test results): **Logistic Regression – Pure Hybrid**.
- Highest test F1 among the 12 models: Logistic Regression – Augmented Hybrid (F1 = 0.385). It is reported for information only and was not used for model selection.
- **Logistic Regression** (primary): AUROC +0.003 (no clear difference); AUPRC +0.005 (no clear difference); F1 +0.005 (no clear difference); Recall -0.036 (decline)
- **Random Forest**: AUROC +0.001 (no clear difference); AUPRC +0.004 (no clear difference); F1 +0.002 (no clear difference); Recall -0.008 (no clear difference)
- **SVM**: AUROC +0.006 (no clear difference); AUPRC +0.011 (no clear difference); F1 +0.026 (improvement); Recall +0.068 (improvement)
- **XGBoost**: AUROC -0.001 (no clear difference); AUPRC +0.013 (no clear difference); F1 -0.002 (no clear difference); Recall -0.043 (no clear difference)
- The effect of the cluster features was model-specific: some classifier–metric pairs improved and others declined.
- Augmented Hybrid results (with `Cluster_CVD_Rate`) are a secondary analysis and should not be presented as the main hybrid result.

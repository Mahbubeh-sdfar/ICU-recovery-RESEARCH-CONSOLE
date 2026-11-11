# Research Methods and Evaluation

## 1. Dataset
The project currently reports **5,000 synthetic patient records** and **53,550 longitudinal observation records**. No real patient records or protected health information are intended to be used.

A complete release should document synthetic-data generation, variable distributions and ranges, dependencies, outcome-generation rules, missingness mechanisms and random seeds. Until then, the data must not be described as clinically representative.

## 2. Prediction tasks

### Uncontrolled postoperative pain
A binary prediction task for records labelled as uncontrolled postoperative pain. The implementation documentation must specify the operational outcome definition, observation window, prediction time, feature availability, repeated-measure handling and class prevalence.

### Delayed first mobilisation
A binary prediction task for records labelled as delayed first mobilisation. The implementation documentation must specify the time origin, operational delay definition, prediction horizon, feature availability, repeated-measure handling and class prevalence.

Both outcome definitions require clinical review before any real-data study.

## 3. Candidate models
- Logistic Regression
- Random Forest
- Histogram-based Gradient Boosting

Logistic Regression is the selected model reported for the current held-out test results. Preserve comparison results for all candidate models when experiment artefacts are released.

## 4. Evaluation design
The reported workflow includes patient-level train/validation/test partitioning, grouped five-fold cross-validation, hyperparameter optimisation, held-out testing, ROC and precision-recall analysis, calibration assessment, confusion matrices, feature importance and SHAP inspection.

Because observations are repeated within patients, splitting should be performed by patient identifier. Preprocessing steps that learn from data (imputation, scaling, encoding and feature selection) should be fitted inside training folds only. Verify that no post-outcome or future information is used as a predictor.

## 5. Reported held-out results

| Outcome | Selected model | AUROC | AUPRC |
|---|---|---:|---:|
| Uncontrolled postoperative pain | Logistic Regression | 0.746 | 0.682 |
| Delayed first mobilisation | Logistic Regression | 0.637 | 0.580 |

For a complete report, also provide test-set size, event prevalence, uncertainty intervals, baseline performance, calibration metrics, threshold-dependent metrics, split seed and data version.

## 6. Interpretation
The pain-task AUROC of 0.746 indicates moderate ranking discrimination in this synthetic test setting. The delayed-mobilisation AUROC of 0.637 indicates more limited discrimination in the same setting.

AUPRC depends on outcome prevalence and should be interpreted alongside positive-class prevalence and a baseline precision reference. Neither AUROC nor AUPRC alone demonstrates calibration, clinical utility or patient benefit. Feature importance and SHAP describe fitted-model behaviour; they do not establish causality.

Do not compare these values directly with published clinical models unless datasets, outcomes, prediction times and evaluation protocols are sufficiently comparable.

## 7. Reproducibility requirements
Release the synthetic-data generation specification, data dictionary, target definitions, pinned environment, training/evaluation entry points, random seeds, split identifiers, hyperparameters, machine-readable metrics and figures generated from those metrics. See [Reproducibility Checklist](REPRODUCIBILITY.md).

## 8. Limitations
- Synthetic data may not reproduce real case mix, measurement error, missingness, workflow or outcome prevalence.
- Patient-level splitting reduces one form of leakage but cannot rule out all design bias.
- Current metrics do not establish external validity.
- Clinical utility and improved recovery have not been demonstrated.
- Explanations are not causal.
- LLM responses may be incorrect or incomplete despite retrieval and citation checks.

## 9. Proposed next steps
1. Publish synthetic-data generation methods and precise outcome definitions.
2. Add uncertainty intervals and prevalence-aware baselines.
3. Conduct error and subgroup analyses where appropriate.
4. Obtain clinical review of predictors, outcomes and prediction timing.
5. Design external validation using appropriately governed data.
6. Consider prospective feasibility only after validation planning and relevant approvals.

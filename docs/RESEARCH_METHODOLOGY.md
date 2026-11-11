
# Research Methodology

## 1. Research Objective

This project explores the application of machine learning and AI-assisted evidence retrieval to postoperative recovery research.

Two prediction tasks are investigated:

1. Uncontrolled postoperative pain.
2. Delayed first mobilisation.

The broader objective is to investigate how longitudinal postoperative observations and interpretable predictive models can contribute to research into individualized recovery monitoring.

## 2. Study Design

This is a computational research prototype based on a synthetic longitudinal dataset.

The experimental workflow includes:

- Synthetic patient data generation.
- Patient-level data partitioning.
- Prediction feature construction.
- Supervised machine-learning experiments.
- Model evaluation and interpretation.
- Integration of prediction outputs into an evidence-assisted software workflow.

No real patient records were used.

## 3. Dataset Characteristics

The project dataset is located at:

`data/synthetic_icu_patients.csv`

| Characteristic | Description |
|---|---|
| Unique synthetic patients | 5,000 |
| Observation records | 53,550 |
| Number of columns | 36 |
| Observation period | Up to 168 postoperative hours |
| Observation interval | Every 4 simulated hours |
| Default training patients | 4,000 |
| Default test patients | 1,000 |

The dataset includes simulated demographic characteristics, surgical information, comorbidities, physiological observations, pain assessments, sedation, medication exposures, mobility-related variables, and recovery outcomes.

For further variable definitions, see `data/data_dictionary.md`.

## 4. Prediction Time and Temporal Feature Construction

The prediction index is set at 6 postoperative hours.

The default observation cadence means that eligible longitudinal observations at the prediction index are available at hours 0 and 4.

Feature construction uses baseline characteristics and eligible observations available at or before the prediction time.

The dataset service organizes observations chronologically and constructs patient-level prediction features.

This temporal restriction is intended to reduce information leakage from future observations.

Future outcome information, target labels, and length-of-stay information should not be used as predictors.

## 5. Prediction Tasks

### 5.1 Uncontrolled Postoperative Pain

The project-specific synthetic target is defined using assessments strictly after hour 6 and through hour 24.

A positive label is assigned when at least one eligible assessment meets either condition:

- NRS pain score ≥ 4.
- CPOT score ≥ 3 when NRS is not applicable.

The target is left missing when no eligible assessment is available in the specified outcome window.

This is an operational definition used to construct the synthetic research label, not a universal clinical threshold or treatment recommendation.

### 5.2 Delayed First Mobilisation

This task investigates the prediction of a delayed first-mobilisation outcome using the project-defined synthetic target.

The exact operational definition, threshold, and observation window should be interpreted according to the current `data/data_dictionary.md` specification.

The target represents a simulated research outcome and must not be interpreted as a clinical mobilisation-safety assessment.

## 6. Data Partitioning

The default dataset generation process creates patient-level training and test partitions.

| Partition | Patients |
|---|---:|
| Training | 4,000 |
| Test | 1,000 |
| Total | 5,000 |

All observations belonging to an individual patient remain in the same partition.

This prevents observations from the same simulated patient from appearing in both training and test sets.

The documented modelling workflow also includes grouped cross-validation and model-selection procedures.

## 7. Machine-Learning Models

The investigated candidate algorithms include:

### Logistic Regression
Used as an interpretable baseline model for binary prediction.

### Random Forest
Used to investigate nonlinear relationships and interactions between features.

### Histogram-based Gradient Boosting
Used as a gradient-boosting candidate for structured tabular data.

Model selection and evaluation should be performed independently for each prediction task.

## 8. Model Evaluation

The documented experimental workflow includes:

- Area Under the Receiver Operating Characteristic Curve (AUROC).
- Area Under the Precision-Recall Curve (AUPRC).
- Calibration analysis.
- Confusion matrices.
- Feature-importance analysis.
- SHAP-based interpretation.

AUROC evaluates ranking discrimination across classification thresholds.

AUPRC is particularly relevant when positive and negative outcome frequencies are imbalanced. It should be interpreted alongside the positive-class prevalence.

Calibration analysis investigates agreement between predicted probabilities and observed outcome frequencies.

No single metric establishes clinical usefulness.

## 9. Explainability

Feature-importance and SHAP analyses are used to examine the contribution of input variables to model predictions.

These analyses can help identify influential features and support model inspection.

However, predictive feature contributions do not demonstrate causation or establish that modifying a feature will improve recovery.

## 10. Reproducibility

The synthetic dataset generator is:

`data/generate_synthetic_icu.mjs`

The documented default random seed is:

`20261102`

The generator supports alternative seeds, patient counts, and output locations.

For environment setup, experiment execution, and configuration, consult the project implementation and `docs/REPRODUCIBILITY.md`.

## 11. Methodological Limitations

The dataset is generated using hand-designed simulation mechanisms with random variation. Its relationships are not fitted or calibrated to real clinical populations.

Consequently:

- Synthetic distributions may not represent real ICU populations.
- Simulated associations may not reflect clinical relationships.
- Model performance may differ substantially on real-world data.
- Synthetic test-set performance cannot establish external validity.
- The findings should be treated as methodological demonstrations.

## 12. Future Research

Future investigations could explore:

- External validation using appropriately governed clinical datasets.
- Temporal machine-learning approaches.
- Personalized postoperative risk estimation.
- Functional recovery and mobility measurements.
- Integration of wearable sensor data.
- Relationships between postoperative recovery and rehabilitation outcomes.
- Prospective evaluation with clinical and rehabilitation researchers.

---

**Document status:** Methodological description of a synthetic-data research prototype. Not a clinical validation study.

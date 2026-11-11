
# Model Evaluation

## 1. Overview

This document summarizes the machine-learning experiments reported for the ICU Recovery Research Console.

The experiments investigate two binary prediction tasks using a synthetic longitudinal postoperative dataset:

1. Uncontrolled postoperative pain.
2. Delayed first mobilisation.

All reported performance results relate to synthetic data.

## 2. Candidate Models

The project investigates three machine-learning algorithms:

| Model | Role |
|---|---|
| Logistic Regression | Interpretable baseline |
| Random Forest | Tree-based ensemble |
| Histogram-based Gradient Boosting | Gradient-boosting model |

The modelling workflow includes grouped validation and model-selection procedures.

## 3. Evaluation Metrics

### AUROC

Area Under the Receiver Operating Characteristic Curve measures the ability of a model to rank positive cases above negative cases across classification thresholds.

### AUPRC

Area Under the Precision-Recall Curve summarizes the relationship between precision and recall.

It is particularly important to interpret this metric alongside the prevalence of the positive class.

### Calibration

Calibration analysis examines whether predicted probabilities correspond to observed outcome frequencies.

### Confusion Matrix

Confusion matrices summarize classification outcomes at a selected threshold, including true positives, false positives, true negatives, and false negatives.

## 4. Reported Results

The following Logistic Regression results are reported for held-out synthetic test data.

| Prediction task | AUROC | AUPRC |
|---|---:|---:|
| Uncontrolled postoperative pain | 0.746 | 0.682 |
| Delayed first mobilisation | 0.637 | 0.580 |

These values are reported experimental results, not evidence of clinical performance.

## 5. Interpretation

### Uncontrolled Postoperative Pain

The reported AUROC of 0.746 indicates discrimination within the simulated test dataset.

The AUPRC of 0.682 should be considered in relation to the positive-class prevalence.

### Delayed First Mobilisation

The reported AUROC of 0.637 indicates more limited discrimination within the simulated test dataset.

Further investigation would be required to understand feature contributions, outcome construction, and model behaviour.

## 6. Explainability

The project incorporates:

- Feature-importance analysis.
- SHAP-based interpretation.

These methods support inspection of model behaviour but do not demonstrate causality.

## 7. Important Interpretation Restrictions

The results must not be interpreted as:

- Clinical accuracy.
- External validation.
- Evidence of patient benefit.
- Proof of clinical utility.
- Evidence that the models are suitable for treatment decisions.

The dataset is synthetic and uses hand-designed simulation mechanisms rather than relationships calibrated against real clinical populations.

## 8. Future Evaluation

Future evaluation should include:

- Validation on appropriately governed real-world data.
- Independent external testing.
- Calibration assessment in target populations.
- Subgroup performance analysis.
- Assessment of missing-data robustness.
- Decision-curve and clinical utility studies where appropriate.
- Prospective evaluation with clinical collaborators.

---

**Evaluation status:** Preliminary synthetic-data experiments. No clinical validation has been performed.

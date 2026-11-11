
# Limitations, Ethics, and Responsible Use

## 1. Research Status

The ICU Recovery Research Console is a research and software-development prototype.

It has been developed to explore machine learning, explainable AI, evidence retrieval, and AI-assisted information processing in postoperative recovery research.

It is not a clinically validated medical device or clinical decision-support system.

## 2. Synthetic Data

All patient records used in this project are synthetic.

The dataset contains 5,000 simulated patients and 53,550 longitudinal observation records.

Its relationships are generated through hand-designed simulation mechanisms with random variation.

They are not fitted or calibrated to real clinical populations.

Consequently, the dataset cannot establish how real patients behave or how models would perform in actual healthcare settings.

## 3. Model Performance Limitations

Reported model results are based on held-out synthetic test data.

They cannot establish:

- Real-world predictive accuracy.
- External validity.
- Clinical usefulness.
- Patient benefit.
- Generalizability across hospitals or patient populations.

Performance may change substantially when models are evaluated on real clinical data.

## 4. Outcome Definition Limitations

The prediction targets are project-specific synthetic labels.

The uncontrolled-pain target uses the project's defined NRS and CPOT thresholds and observation window.

The delayed-mobilisation target follows the operational definition in the project data dictionary.

These labels are research constructs and must not be interpreted as universal clinical definitions or treatment criteria.

## 5. Explainability Limitations

SHAP and feature-importance methods help investigate model behaviour.

However:

- Feature importance does not establish causation.
- Explanations may depend on the model and data distribution.
- An influential feature is not necessarily clinically modifiable.
- Explanations do not guarantee that a prediction is correct.

## 6. AI Agent Safety

The AI workflow combines synthetic patient context, research predictions, and retrieved evidence.

The implementation includes safeguards such as:

- Data validation.
- Clarification when required information is missing.
- Abstention when evidence is insufficient.
- Citation verification.
- Restrictions against medication orders and treatment instructions.

These safeguards reduce certain software-level risks but do not establish clinical safety.

Language models can still generate inaccurate or misleading content.

Human clinical oversight would be essential in any future clinical research deployment.

## 7. Privacy and Data Governance

The public demonstration uses synthetic data rather than real patient records.

Any future use of real clinical information would require appropriate:

- Institutional approvals.
- Data protection safeguards.
- Consent or other lawful data-processing basis.
- Access controls.
- Secure storage.
- Data minimization.
- Governance and audit procedures.

No real patient information should be uploaded to the public repository.

## 8. Clinical and Rehabilitation Boundaries

The project investigates postoperative pain and delayed first mobilisation.

It does not currently demonstrate:

- Validated mobility assessment.
- Gait analysis.
- Pose-estimation-based rehabilitation.
- Mobilisation safety assessment.
- Clinical rehabilitation effectiveness.
- Personalized treatment prescription.

These are possible future research directions, not established capabilities of the current prototype.

## 9. Future Research Requirements

Before any clinical application could be considered, further work would be necessary:

1. Validate outcome definitions with clinical experts.
2. Evaluate models using appropriately governed real-world datasets.
3. Perform independent external validation.
4. Examine subgroup performance and potential bias.
5. Evaluate calibration and clinical utility.
6. Assess human factors and workflow integration.
7. Conduct prospective evaluation under appropriate oversight.

## 10. Responsible Use Statement

This repository is provided for research, education, and software experimentation.

It must not be used to diagnose patients, recommend treatment, determine medication doses, or make patient-care decisions.

The software does not replace clinical judgement or professional healthcare assessment.

---

**Ethical status:** Synthetic-data research prototype. No clinical validation or authorization for patient-care use.

# Reproducibility Checklist

Use this checklist before describing the experiments as independently reproducible.

## Dataset and outcomes
- [ ] Publish a data dictionary with units and valid ranges.
- [ ] Document generation of 5,000 synthetic patient records.
- [ ] Document generation/linkage of 53,550 longitudinal observations.
- [ ] Describe variable distributions, dependencies, noise and missingness.
- [ ] Define uncontrolled postoperative pain operationally.
- [ ] Define delayed first mobilisation operationally.
- [ ] State prediction time, prediction horizon and feature-availability window.
- [ ] Record class prevalence and patient/observation counts per split.

## Splitting and preprocessing
- [ ] Record split proportions, random seed and patient IDs per partition.
- [ ] Confirm no patient appears in multiple partitions.
- [ ] Fit imputation, scaling, encoding and feature selection within training folds only.
- [ ] Check for post-outcome and future-information leakage.
- [ ] Document handling of repeated and time-dependent observations.

## Model training
- [ ] Record model implementations and package versions.
- [ ] Record hyperparameter search spaces and selection criteria.
- [ ] Document class-imbalance handling, if used.
- [ ] Record threshold-selection procedure.
- [ ] Preserve Logistic Regression, Random Forest and Histogram-based Gradient Boosting comparisons.
- [ ] Save model configurations and artefact identifiers.

## Evaluation
- [ ] Report AUROC and AUPRC with positive-class prevalence.
- [ ] Add uncertainty intervals and baseline comparisons.
- [ ] Report calibration metrics and plots.
- [ ] Report confusion matrices and threshold-dependent metrics.
- [ ] Include error analysis and explainability outputs.
- [ ] Generate figures/tables from machine-readable outputs.
- [ ] State clearly that current metrics are from synthetic data.

## Retrieval and LLM workflow
- [ ] Record document sources, versions, licences and access dates.
- [ ] Record chunking strategy and embedding model.
- [ ] Record vector index configuration and retrieval parameters.
- [ ] Record Ollama model name/version and runtime settings.
- [ ] Document LangGraph nodes, state transitions and failure handling.
- [ ] Test citation checks against supported and unsupported claims.
- [ ] Test missing-information and retrieval-failure behaviour.

## Software environment
- [ ] Add pinned dependencies or a lockfile.
- [ ] Document Python and Node.js versions.
- [ ] Provide a safe .env.example containing variable names only.
- [ ] Document database setup and migrations.
- [ ] Provide verified installation/run commands.
- [ ] Add unit, integration and application smoke tests.

## Research integrity and safety
- [ ] State that current evaluation data are synthetic.
- [ ] State that clinical validation has not been performed.
- [ ] Do not claim clinical effectiveness or patient benefit.
- [ ] Do not include identifiable patient information or secrets.
- [ ] Obtain ethics, governance and data-access approvals before real-data work.
- [ ] Obtain clinical review of outcome definitions and intended use.

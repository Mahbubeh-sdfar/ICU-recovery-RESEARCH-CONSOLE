# ICU Pain & Recovery Assistant
### An AI-assisted research prototype for postoperative pain and early mobilisation risk

[![Status](https://img.shields.io/badge/status-research%20prototype-blue)](#project-status)
[![Data](https://img.shields.io/badge/data-synthetic-orange)](#data-and-privacy)
[![Clinical validation](https://img.shields.io/badge/clinical%20validation-not%20performed-lightgrey)](#limitations)

## Overview
The ICU Pain & Recovery Assistant is a research-oriented software prototype exploring how machine learning and evidence-retrieval workflows could support investigation of two early postoperative recovery risks:

1. **Uncontrolled postoperative pain**
2. **Delayed first mobilisation**

The project combines tabular machine-learning models, explainability methods, retrieval-augmented generation (RAG), and an LLM-assisted evidence workflow. Its research motivation is to explore how structured observations and relevant evidence might support investigation of postoperative recovery.

**This is an experimental prototype. It is not a medical device, a clinically validated decision-support system, or a tool for patient care.**

## Research questions
- Can structured postoperative variables discriminate between outcome classes in this synthetic dataset?
- How do interpretable baseline models compare with tree-based models?
- Can model explanations make predictions easier to inspect?
- Can retrieved clinical documents be connected to an LLM workflow with visible source passages and checks for unsupported responses?

## Dataset and reported results
The current project description reports **5,000 synthetic patient records** and **53,550 longitudinal observation records**.

| Prediction task | Selected model | AUROC | AUPRC |
|---|---|---:|---:|
| Uncontrolled postoperative pain | Logistic Regression | 0.746 | 0.682 |
| Delayed first mobilisation | Logistic Regression | 0.637 | 0.580 |

These are reported held-out test results on synthetic data only. They do not estimate performance in a real hospital population, establish clinical utility, or demonstrate improved patient outcomes. AUPRC should be interpreted alongside event prevalence.

## Methods and technical components
- **Models:** Logistic Regression, Random Forest and Histogram-based Gradient Boosting.
- **Evaluation:** patient-level train/validation/test split, grouped five-fold cross-validation, hyperparameter optimisation, ROC/PR analysis, calibration and confusion matrices.
- **Explainability:** feature importance and SHAP.
- **Agent workflow:** LangGraph orchestration and local LLM inference through Ollama.
- **Evidence layer:** PostgreSQL with pgvector, retrieval-augmented generation, passage/citation checks and missing-information prompts.
- **Application:** Python, scikit-learn, SHAP, FastAPI, React and TypeScript.

## Architecture
See [Architecture](docs/ARCHITECTURE.md) for component, modelling and evidence-flow diagrams.

## Intended research workflow
1. Define the outcome and prediction time.
2. Prepare synthetic patient and longitudinal observation data.
3. Split data at patient level to reduce leakage across repeated observations.
4. Train and tune candidate models within training data.
5. Evaluate on held-out patients using discrimination, precision-recall, calibration and error metrics.
6. Inspect model behaviour and feature contributions.
7. Retrieve relevant documents for evidence-assisted exploration.
8. Review outputs critically; do not use them for patient-care decisions.

## Project status
**Research prototype.** This is an individual research-oriented prototype developed to explore critical care, postoperative recovery, machine learning and evidence-assisted clinical workflows. AI coding tools, including Codex, were used to support parts of implementation and debugging. This is not a claim of sole manual implementation of every software component.

The public source tree should be checked against the recommended layout in [Repository Structure](docs/REPOSITORY_STRUCTURE.md). The proposed layout is not a claim that all directories have already been extracted from the packaged source archive.

## Data and privacy
- The reported evaluation dataset is synthetic.
- Do not commit real patient records or protected health information.
- Do not upload credentials, API keys, local environment files or private clinical documents.
- Check licences and permitted use before adding external documents to the retrieval knowledge base.

## Limitations
1. **No clinical validation:** no prospective or retrospective real-world validation has been reported.
2. **Synthetic-data limitation:** performance on simulated records may not generalise to any hospital or patient group.
3. **Outcome definitions:** prediction horizons, feature availability and target definitions require explicit documentation and clinical review.
4. **Potential bias and leakage:** patient-level splitting does not rule out all leakage, confounding or sampling bias.
5. **LLM limitations:** generated text may be incorrect or incomplete despite retrieval and citation checks.
6. **Human oversight:** the prototype must not diagnose, prescribe, triage, delay care or replace clinical judgement.

## Documentation
- [Project overview](docs/PROJECT_OVERVIEW.md)
- [Architecture and diagrams](docs/ARCHITECTURE.md)
- [Research methods and evaluation](docs/RESEARCH_AND_EVALUATION.md)
- [Recommended repository structure](docs/REPOSITORY_STRUCTURE.md)
- [Reproducibility checklist](docs/REPRODUCIBILITY.md)

## Roadmap
- [ ] Extract and publish the readable source tree.
- [ ] Add a tested dependency specification and verified installation instructions.
- [ ] Document target definitions, feature lists, prediction horizons and missing-data handling.
- [ ] Add a data dictionary and synthetic-data generation description.
- [ ] Add scripts/notebooks that reproduce the reported evaluation results.
- [ ] Add unit tests and an end-to-end smoke test.
- [ ] Add non-sensitive screenshots.
- [ ] Plan external validation with appropriate governance, ethics and data-access approvals.
- [ ] Obtain clinical and methodological review before considering real-world use.

## Citation
For now, cite the repository URL and the version/date inspected. Add a formal software citation file after author/contributor metadata and release version are confirmed.

**Research focus:** postoperative recovery, early mobilisation, critical care, interpretable machine learning and evidence-assisted digital health.

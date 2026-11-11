# Project Overview

## Identity
**ICU Pain & Recovery Assistant** is a research-oriented software prototype exploring machine learning and evidence-assisted workflows for two postoperative recovery outcomes: uncontrolled postoperative pain and delayed first mobilisation.

**Domain:** critical care, postoperative recovery, clinical machine learning, explainable AI and digital health.  
**Data:** synthetic only.  
**Status:** not clinically validated; not intended for patient care.

## Motivation and aims
Postoperative recovery involves pain control, physiological stability and the ability to begin mobilisation. This prototype explores whether structured longitudinal observations can support exploratory risk modelling, and whether model explanations and retrieved evidence can make a research workflow more inspectable.

Aims:
1. Build and evaluate baseline models for two postoperative recovery-related outcomes.
2. Explore model interpretability and error analysis.
3. Prototype a retrieval-grounded LLM workflow that exposes supporting passages.
4. Create a foundation for future review and collaboration across clinical, rehabilitation and data-science disciplines.

## Research questions
- What discrimination can candidate models achieve on the synthetic dataset?
- How do linear and tree-based models compare under patient-level evaluation?
- Which features influence model predictions, and what requires clinical review?
- Can retrieved passages and citation checks improve the inspectability of LLM-assisted responses?
- What additional data, outcome definitions and validation would be needed before a real-world study?

## Scope
**Included:** two prediction tasks; 5,000 synthetic patient records and 53,550 longitudinal observations; Logistic Regression, Random Forest and Histogram-based Gradient Boosting; patient-level splitting; grouped five-fold cross-validation; hyperparameter optimisation; ROC/PR, calibration and confusion-matrix analyses; feature importance and SHAP; LangGraph, Ollama, PostgreSQL/pgvector, FastAPI and React/TypeScript components.

**Not included:** clinical deployment, prospective recruitment, real-patient validation, automated diagnosis or triage, treatment recommendations, gait or movement-quality measurement, or evidence of improved patient outcomes.

## Intended audience
Researchers and collaborators interested in critical care, postoperative recovery, clinical machine learning, explainable AI and evidence-assisted digital health. The prototype also serves as an interdisciplinary research and technical portfolio artefact.

## Current evidence
The currently reported held-out results are described in [Research and Evaluation](RESEARCH_AND_EVALUATION.md). They are preliminary experiments on synthetic data, not evidence of external validity, clinical utility or patient benefit.

## Development principles
- **Transparency:** distinguish implemented components from planned work.
- **Reproducibility:** record data generation, target definitions, splits, features, configurations and software versions.
- **Patient-level separation:** keep repeated observations from a patient within one partition.
- **Interpretability:** treat feature attribution as model explanation, not causal inference.
- **Evidence traceability:** expose retrieved passages and source metadata.
- **Safety:** preserve human oversight and state limitations clearly.

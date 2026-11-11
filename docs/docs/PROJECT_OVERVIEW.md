
# Project Overview

## ICU Recovery Research Console

The ICU Recovery Research Console is an interdisciplinary research and software-development prototype exploring the use of machine learning, explainable AI, evidence retrieval, and AI agent workflows in postoperative recovery research.

The project investigates two prediction tasks:

1. Uncontrolled postoperative pain.
2. Delayed first mobilisation.

It aims to connect longitudinal synthetic patient data, predictive modelling, and evidence-assisted information retrieval within a modular software environment.

## 1. Research Motivation

Postoperative recovery is a complex process influenced by multiple interacting factors, including pain, physiological status, sedation, medication exposure, and functional recovery.

Identifying patterns associated with adverse recovery outcomes may help researchers investigate more personalized approaches to postoperative monitoring and rehabilitation.

This project explores the technical feasibility of combining predictive modelling with evidence retrieval and AI-assisted information processing.

## 2. Research Objectives

The main objectives are:

- Develop a synthetic longitudinal dataset for postoperative recovery research.
- Investigate machine-learning approaches to selected recovery prediction tasks.
- Explore explainable AI methods for interpreting model behaviour.
- Develop an evidence retrieval pipeline using clinical literature.
- Integrate predictive outputs and retrieved evidence into a safety-constrained AI workflow.
- Demonstrate a modular full-stack research application.

## 3. Main Research Components

### Synthetic Clinical Data

The project includes 5,000 simulated patients and 53,550 longitudinal observation records.

The dataset contains simulated demographic, surgical, physiological, pain, medication, sedation, mobility, and outcome-related variables.

### Predictive Modelling

The machine-learning pipeline investigates:

- Uncontrolled postoperative pain.
- Delayed first mobilisation.

Candidate models include Logistic Regression, Random Forest, and Histogram-based Gradient Boosting.

### Explainable AI

Feature importance and SHAP-based analysis are used to investigate model behaviour and influential predictive features.

### Evidence Retrieval

A retrieval-augmented generation pipeline extracts, indexes, and retrieves relevant passages from research documents.

Retrieved passages retain source information to support traceability.

### AI Agent Workflow

A LangGraph-based workflow coordinates patient context, data validation, existing model predictions, evidence retrieval, response generation, and safety verification.

## 4. Technical Implementation

| Layer | Technologies |
|---|---|
| Frontend | React, TypeScript, Vite |
| Backend | Python, FastAPI |
| Database | PostgreSQL, pgvector |
| Database management | SQLAlchemy, Alembic |
| Machine learning | scikit-learn |
| Explainability | SHAP |
| Agent orchestration | LangGraph |
| Local LLM | Ollama, Gemma 3:4b |
| Embeddings | nomic-embed-text |
| Document extraction | PyMuPDF |
| Visualization | Recharts |
| Infrastructure | Docker Compose |

## 5. Demonstrated Project Status

The local demonstration report dated November 4, 2026 documents:

- Integration of the frontend and backend.
- PostgreSQL and pgvector database configuration.
- Import of 5,000 synthetic patients and 53,550 observations.
- Evidence ingestion and vector retrieval.
- Local language-model integration.
- 38 passing backend tests.
- A successful frontend production build.

These results demonstrate software implementation and selected integration tests, not clinical validation.

## 6. Research Relevance

The project connects several research areas:

- Digital health.
- Clinical machine learning.
- Explainable artificial intelligence.
- Postoperative and critical-care recovery.
- Evidence-assisted AI systems.
- Functional recovery and rehabilitation technology.

The broader research direction is to explore how technology-enabled approaches could support more personalized postoperative recovery and rehabilitation research.

## 7. Current Limitations

The project uses entirely synthetic patient data.

Its simulated relationships are hand-designed and are not calibrated to real clinical populations.

The model results therefore cannot establish clinical accuracy, generalizability, or patient benefit.

The software is a research prototype and is not intended for clinical decision-making.

## 8. Future Research

Potential future directions include:

- Evaluation using appropriately governed real-world clinical datasets.
- External validation of prediction models.
- Temporal modelling of postoperative recovery.
- Integration of functional mobility measurements.
- Wearable sensor and movement-analysis research.
- Personalized rehabilitation research.
- Prospective collaboration with clinical and rehabilitation teams.

## Project Status

Research prototype — synthetic-data experiments and local software integration demonstrated. Clinical validation remains future work.

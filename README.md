
# ICU Recovery Research Console
### An AI-assisted research prototype for exploring postoperative recovery

An interdisciplinary research and software-development project exploring how machine learning, explainable AI, and evidence retrieval can support research into postoperative recovery.

The project focuses on two prediction tasks:
- Uncontrolled postoperative pain
- Delayed first mobilisation

It integrates predictive modelling with an evidence-assisted AI workflow in a locally deployable software environment.

> **Research status:** This is a research prototype evaluated using entirely synthetic data. It has not undergone clinical validation and must not be used for patient-care decisions.

---

## Research motivation

Postoperative recovery involves multiple interacting factors, including pain, sedation, physiological status, medication exposure, and functional recovery.

This project explores a technology-enabled approach to organising these data and investigating whether machine-learning methods can identify patterns associated with selected recovery outcomes.

The broader research motivation is to connect clinical experience in anesthesia and perioperative care with digital health, personalized recovery research, and rehabilitation technology.

## Main components

### 1. Synthetic clinical dataset
- 5,000 simulated patients
- 53,550 longitudinal observation records
- Repeated postoperative observations
- Patient-level training and test separation
- Synthetic clinical variables and outcome labels

### 2. Machine-learning experiments
The project explores prediction of:
- Uncontrolled postoperative pain
- Delayed first mobilisation

Candidate algorithms include:
- Logistic Regression
- Random Forest
- Histogram-based Gradient Boosting

### 3. Explainable AI
Model interpretation includes:
- Feature importance
- SHAP-based analysis

### 4. Evidence retrieval
A retrieval-augmented generation (RAG) workflow uses indexed evidence passages and source provenance to support evidence-oriented responses.

### 5. AI agent workflow
A LangGraph-based workflow integrates:
- Query classification
- Synthetic patient context
- Data validation
- Model predictions
- Evidence retrieval
- Response generation
- Safety verification

The workflow includes safeguards against unsupported evidence claims and treatment or order instructions.

## Preliminary model results

The following are reported held-out test results from experiments using the synthetic dataset.

| Prediction task | Model | AUROC | AUPRC |
|---|---|---:|---:|
| Uncontrolled postoperative pain | Logistic Regression | 0.746 | 0.682 |
| Delayed first mobilisation | Logistic Regression | 0.637 | 0.580 |

These results describe performance on simulated data only. They do not establish clinical accuracy, generalizability, or clinical utility. AUPRC should also be interpreted in relation to the positive-class prevalence.

## Technology stack

| Component | Technologies |
|---|---|
| Backend | Python, FastAPI |
| Frontend | React, TypeScript, Vite |
| Database | PostgreSQL, pgvector |
| Database migrations | SQLAlchemy, Alembic |
| Machine learning | scikit-learn |
| Explainability | SHAP |
| Agent orchestration | LangGraph |
| Local language models | Ollama |
| Embeddings | nomic-embed-text |
| Evidence extraction | PyMuPDF |
| Visualization | Recharts |
| Deployment support | Docker Compose |

## Demonstration and testing

The project demonstration report dated November 4, 2026 documents:
- 38 passing backend tests
- A successful frontend production build
- A local integration of the frontend, backend, database, machine-learning and evidence-retrieval components
- A synthetic dataset imported into PostgreSQL with pgvector
- A demonstration of citation verification that withheld an AI-generated draft when its citations could not be verified

These are software integration and testing results, not clinical validation.

See [research_demonstration_report.md](research_demonstration_report.md).

## Repository structure

```text
.
├── backend/
├── frontend/
├── data/
├── docs/
├── README.md
├── research_demonstration_report.md
├── spec.md
└── spec_change_summary.md
```

The `docs/` directory contains the research methodology, architecture, evaluation, reproducibility, and limitations documentation.

## Research limitations

- All patient records are synthetic.
- Simulated relationships are not calibrated to real clinical populations.
- Model results cannot be interpreted as real-world clinical performance.
- The project is not a medical device or validated clinical decision-support system.
- The AI workflow does not replace clinical judgement.
- Further research requires appropriate real-world datasets, external validation, and clinical collaboration.

## Future research directions

Potential directions include:
- Validation using appropriately governed clinical datasets
- Improved temporal modelling of postoperative recovery
- Personalized risk estimation
- Integration of functional recovery and mobility measures
- Exploration of links between postoperative recovery and technology-enabled rehabilitation
- Prospective evaluation with clinical and rehabilitation researchers

## Author's research interests

This project reflects an interest in the intersection of:

- Digital health and clinical AI
- Postoperative and critical-care recovery
- Explainable machine learning
- Evidence-assisted clinical research
- Technology-enabled personalized rehabilitation

## Project status

Research prototype — synthetic-data experiments and local software integration demonstrated. Clinical validation remains future work.

## Documentation

| Document | Description |
|---|---|
| [Project Overview](docs/PROJECT_OVERVIEW.md) | Research objectives, motivation and scope |
| [System Architecture](docs/SYSTEM_ARCHITECTURE.md) | Technical architecture and agent workflow |
| [Research Methodology](docs/RESEARCH_METHODOLOGY.md) | Dataset, prediction tasks and experimental design |
| [Model Evaluation](docs/MODEL_EVALUATION.md) | Models, metrics and reported results |
| [Reproducibility](docs/REPRODUCIBILITY.md) | Dataset generation and technical environment |
| [Limitations and Ethics](docs/LIMITATIONS_AND_ETHICS.md) | Research limitations and responsible use |
| [Demonstration Report](research_demonstration_report.md) | Documented software integration and testing |


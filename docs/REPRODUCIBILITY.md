
# Reproducibility and Technical Setup

## 1. Purpose

This document describes the available project components and the information required to reproduce the synthetic-data and software demonstration environment.

The project is intended for research and software experimentation.

## 2. Repository Components

| Directory or file | Purpose |
|---|---|
| `backend/` | API, data services, machine learning, database and agent workflow |
| `frontend/` | React and TypeScript application |
| `data/` | Synthetic dataset, generator and data dictionary |
| `backend/tests/` | Backend automated tests |
| `backend/migrations/` | Database migration files |
| `backend/reports/` | Research and evaluation outputs |
| `backend/research_corpus/` | Evidence document resources |
| `research_demonstration_report.md` | Documented local integration results |

## 3. Synthetic Dataset Generation

The generator is:

`data/generate_synthetic_icu.mjs`

The documented default random seed is:

`20261102`

From the repository root, the default generation command is:

```bash
node data/generate_synthetic_icu.mjs
```

The generator also supports optional arguments:

- `--seed`
- `--patients`
- `--output`

Consult the generator source for exact argument syntax and output behaviour before using custom options.

## 4. Backend Environment

The backend uses Python and includes dependencies for:

- FastAPI.
- SQLAlchemy.
- Alembic.
- scikit-learn.
- pandas.
- SHAP.
- LangGraph.
- PyMuPDF.
- PostgreSQL and pgvector integration.

The dependency list is maintained in:

`backend/requirements.txt`

Use an isolated Python environment when installing dependencies.

## 5. Database Infrastructure

The project includes Docker Compose configuration for PostgreSQL with pgvector.

The documented local database infrastructure uses:

`backend/docker-compose.yml`

The configuration requires a local environment file containing the required database configuration, including `POSTGRES_PASSWORD`.

Do not commit credentials, passwords, API keys, or private environment files to the public repository.

Database schema migrations are maintained under:

`backend/migrations/`

Alembic is used for database migration management.

## 6. Frontend Environment

The frontend uses:

- React.
- TypeScript.
- Vite.
- Recharts.

Frontend dependencies and scripts are defined in the frontend package configuration.

Use the scripts declared in `frontend/package.json` for development and production builds.

## 7. Local AI Infrastructure

The documented demonstration uses Ollama.

Models used include:

- `gemma3:4b`
- `nomic-embed-text`

The embedding model is used to generate text representations for evidence retrieval.

The documented database schema uses 768-dimensional vectors.

Model availability and resource requirements depend on the local machine.

## 8. Evidence Retrieval

The documented workflow includes:

1. Document extraction using PyMuPDF.
2. Passage preparation.
3. Embedding generation.
4. Vector storage in PostgreSQL with pgvector.
5. Semantic retrieval.
6. Source provenance preservation.

The demonstration report documents an ingested source corpus and traceable retrieved passages.

## 9. Testing and Demonstration

The research demonstration report dated November 4, 2026 documents:

- 38 passing backend tests.
- Successful frontend production build.
- Successful synthetic-data import.
- Database migration and validation.
- Vector retrieval.
- Local AI workflow integration.

These results describe the documented demonstration environment and should not be assumed to represent a fresh test run on every machine.

## 10. Reproducibility Considerations

For repeatable experiments, record:

- Dataset generator version.
- Random seed.
- Patient count.
- Dataset version.
- Feature definitions.
- Prediction time.
- Model algorithm and hyperparameters.
- Training and test partition.
- Software dependencies.
- Local model versions.
- Evaluation metrics.

## 11. Security Considerations

Before publishing or sharing the repository:

- Remove local `.env` files.
- Do not expose passwords or API keys.
- Avoid uploading real patient information.
- Check generated reports for private data.
- Use synthetic records only in public demonstrations.

---

**Reproducibility status:** Dataset generation and documented local infrastructure are described. Exact environment setup and experiment execution should be verified against the current source configuration.

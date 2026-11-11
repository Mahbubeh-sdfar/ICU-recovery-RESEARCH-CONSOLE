# Repository Structure

## 1. Current snapshot
The repository was previously inspected with a source ZIP archive and a placeholder README at its root. The tree below is a **recommended target structure**, not a claim that all listed files and directories already exist. Confirm actual module names after extracting and inspecting the archive.

## 2. Recommended layout

```text
ICU-recovery-RESEARCH-CONSOLE/
├── README.md
├── LICENSE                         # Only after choosing a licence
├── CITATION.cff                    # After confirming citation metadata
├── .gitignore
├── .env.example                    # Variable names only; no secrets
├── requirements.txt                # Or pyproject.toml plus lockfile
├── docs/
│   ├── PROJECT_OVERVIEW.md
│   ├── ARCHITECTURE.md
│   ├── RESEARCH_AND_EVALUATION.md
│   ├── REPOSITORY_STRUCTURE.md
│   ├── REPRODUCIBILITY.md
│   ├── DATA_DICTIONARY.md          # To be completed from real schema
│   └── figures/
├── data/
│   ├── README.md
│   └── synthetic/                  # Small safe sample only
├── configs/
│   └── example_config.yaml
├── src/
│   └── icu_recovery/
│       ├── data/
│       ├── features/
│       ├── models/
│       ├── evaluation/
│       ├── explainability/
│       ├── retrieval/
│       ├── agents/
│       ├── api/
│       └── common/
├── frontend/
│   ├── package.json
│   └── src/
├── scripts/
│   ├── train_models.py
│   └── evaluate_models.py
├── notebooks/
│   └── README.md
├── tests/
│   ├── unit/
│   ├── integration/
│   └── test_data_safety.py
├── reports/
│   ├── README.md
│   └── figures/
└── .github/
    └── workflows/
        └── tests.yml
```

## 3. Safely migrating the source archive
1. Clone the repository and extract the ZIP into a temporary directory.
2. Inspect the archive and identify backend, frontend, modelling, configuration, data and documentation components.
3. Remove caches, virtual environments, build output, credentials, local databases and private data.
4. Move source files into a logical structure while preserving working imports and runtime behaviour.
5. Add a dependency specification based on the working environment.
6. Test a clean installation and smoke-test the application.
7. Add verified run commands, screenshots and tests.
8. Commit the readable source tree. Keep the ZIP only as an optional versioned release asset if useful.

Do not create empty folders just to make the repository look larger. Each directory should contain real, purposeful files.

## 4. File and data conventions
- Put reusable application code in **src/**, not only in notebooks.
- Use notebooks for exploration, not as the sole record of the analysis.
- Keep configuration templates free of secrets.
- Never commit API keys, tokens, private clinical documents or real patient data.
- Record provenance and licensing for external retrieval documents.
- Keep generated model binaries out of Git unless small, necessary and documented; use release assets or Git LFS for larger artefacts.
- Use descriptive filenames and relative paths.

## 5. Suggested GitHub metadata
**Description:** Research prototype exploring machine learning and evidence-assisted workflows for postoperative pain and delayed first mobilisation using synthetic data.

**Topics:** critical-care, postoperative-recovery, early-mobilisation, clinical-machine-learning, explainable-ai, retrieval-augmented-generation, digital-health, synthetic-data.

Add a licence only after deciding how others may reuse the code. Do not imply that clinical use is permitted.

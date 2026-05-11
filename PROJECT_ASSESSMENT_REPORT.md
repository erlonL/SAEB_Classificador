# Project Assessment Report

## Executive Summary
This repository is an academic machine learning project (UFPB, course context: Aprendizagem de Máquina 2024.1) focused on predicting SAEB student performance using study/social-behavior variables, with explicit intent to avoid socioeconomic variables as the core explanatory axis.

Current state is best characterized as an archived academic deliverable with substantial exploratory and experimental depth: multi-stage data treatment, feature engineering, class restructuring/balancing, and model comparison across ANN, Decision Tree, and SVM.

Major findings:
- The project demonstrates strong methodological breadth for a course deliverable, including preprocessing, feature mapping, model-specific regularization steps, and comparative metrics.
- Experimental artifacts and processed datasets are present, but end-to-end reproducibility is partially constrained by missing raw-data folder state and missing environment/dependency manifest.
- Documentation intent is clear, but practical recovery by a third party would improve with stronger execution instructions and a single canonical run path.

Strengths:
- Clear social/educational motivation and applied objective.
- Coherent experiment chain with progressively transformed datasets.
- Multiple model families implemented with reported quality metrics.

Limitations:
- Reproducibility friction (no `requirements.txt`/`pyproject.toml`; `data/raw` expected by treatment notebooks is absent in current snapshot).
- Notebook sprawl and duplicated exploratory branches increase onboarding effort.

Continuation potential:
- High for academic continuation and portfolio extension, because intermediate datasets and core modeling logic are preserved.
- Moderate for strict reproducibility by new collaborators without environment reconstruction.

---

## Project Mission
Predict student performance outcomes in SAEB (Paraíba subset across multiple years) from questionnaire-derived educational/social-behavior signals, to support earlier pedagogical attention and intervention hypotheses.

**Status:** Confirmed (high confidence)

## Research / Problem Domain
Educational data mining, supervised classification, and applied machine learning for student performance analysis using large-scale public assessment data.

**Status:** Confirmed (high confidence)

## Intended Audience or Stakeholders
Primary audience in repository evidence and user context:
- Professors / academic evaluators
- Secondary: future student collaborators or researchers extending the work

**Status:** Confirmed for primary audience via user confirmation; inferred for secondary audience (medium confidence)

## Functional or Experimental Overview
Observed end-to-end experimental flow:
1. Data acquisition via Base dos Dados query notebook (`data-gathering/download_data.ipynb`) using SAEB source tables.
2. Initial treatment and multi-year harmonization (`treatment_analysis/1_initial-treatment.ipynb`).
3. Column treatment and ordinal/discrete encoding based on question dictionaries (`treatment_analysis/2_columns-treatment.ipynb`).
4. Correlation-oriented feature engineering and feature filtering (`treatment_analysis/3_correlation_featureengineering.ipynb`).
5. Distribution/PCA analysis and class inspection (`treatment_analysis/4_data-analysis.ipynb`).
6. Class restructuring/interposition noise handling and balancing for binary target variant (`treatment_analysis/5_data-interpos.ipynb`).
7. Model training and comparison in final report notebook (`AM_Projeto_Erlon_Lacerda_Maria_Bandeira-v2.ipynb`) with ANN, Decision Tree, and SVM.

**Status:** Confirmed (high confidence)

## Repository / Study Structure Analysis
High-level structure is academically coherent and phase-oriented:
- `data-gathering/`: source query notebook for extraction
- `treatment_analysis/`: ordered preprocessing and analysis notebooks
- `models/`: model-family-specific notebooks (ANN/SVM/DecisionTree)
- `data/`: processed artifacts (cleaned, FE, balanced)
- `docs/`: course instructions PDF, SAEB dictionaries, related paper
- root final notebook: integrated report and main comparative run

Recoverability observations:
- Strong presence of intermediate artifacts (`*.pkl`, treated CSV).
- Missing raw input directory in snapshot (`data/raw`) required by treatment notebooks.
- No explicit dependency lock/manifest.

**Status:** Confirmed (high confidence)

## Technologies, Frameworks, or Methodologies
Core stack observed in notebooks:
- Python + Jupyter
- Pandas, NumPy
- Scikit-learn (SVM, DecisionTree, GridSearchCV, CV utilities, metrics)
- TensorFlow/Keras (ANN)
- imbalanced-learn (undersampling / balancing)
- Matplotlib, Seaborn (analysis/visualization)
- Base dos Dados client (`basedosdados`) + dotenv for data pull

Methodologies:
- Multi-step preprocessing pipeline
- Categorical mapping informed by questionnaire semantics
- Correlation-based feature filtering
- Class balancing and target restructuring for binary setup
- Model-family comparison with quality metrics and overfitting checks (Ein/Eout framing)

**Status:** Confirmed (high confidence)

## Current Maturity Assessment
**Maturity Stage:** Archived academic deliverable (user-confirmed), with characteristics of prototype/experimental validation.

Assessment:
- Not an operational system and not intended as such.
- Strong as a course-level empirical study artifact.
- Suitable for extension into follow-up experiments if reproducibility and packaging are improved.

**Confidence:** High

---

# Scoring

## Complexity Score: 8.3/10
### Rationale
The project combines nontrivial educational-domain framing, longitudinal data handling (multiple SAEB years), custom preprocessing semantics, feature engineering, class handling strategies, and comparative modeling across fundamentally different algorithm families.

### Key Drivers
- Multi-phase experimental design (data gathering -> treatment -> FE -> balancing -> modeling).
- Integration of ANN, Decision Tree (with cost-complexity pruning), and SVM (with CV tuning).
- Domain-informed variable transformations from questionnaire codes.
- Large-sample analysis context (notebook outputs indicate >200k-row processed stages).

### Notable Challenges
- Harmonizing schema and signal quality across years.
- Managing class imbalance and target-definition decisions.
- Preserving interpretability while reducing feature space.

---

## Readiness Score: 7.1/10
### Rationale
For an academic/research deliverable, readiness is solid: objectives are implemented, models are trained/evaluated, and outputs are recorded. However, strict rerun reproducibility is limited by absent environment pinning and missing raw folder state required by early-stage notebooks.

### Missing Elements
- No dependency/environment manifest (`requirements.txt`, `pyproject.toml`, conda env, etc.).
- No single scripted pipeline from raw acquisition to final results.
- `data/raw` expected by treatment notebooks is absent in this repository snapshot.
- Limited explicit instructions on exact rerun order and expected wall-clock/compute requirements.

### Continuation Feasibility
- **Academic continuation:** High (processed datasets and core notebooks are available).
- **Third-party exact reproduction:** Moderate (requires environment reconstruction + raw data regeneration path).

---

## Documentation / Documentability Score: 7.8/10
### Rationale
Intent and narrative are clear, and notebook naming/order substantially aid interpretation. The repository is documentable and recoverable, but consistency and execution instructions are not yet at frictionless-handoff level.

### Recoverability Assessment
- Positive: README states objective and treatment sequence; notebooks are segmented by phase; supporting docs included.
- Limitation: multiple parallel notebooks in `models/` and `temp/` create ambiguity about canonical experiment path.
- Limitation: environment and data bootstrap instructions are incomplete for a fresh machine.

### Suggested Improvements
- Add one canonical how-to-reproduce path (minimal commands + notebook order).
- Add dependency manifest and version notes.
- Mark archival vs experimental notebooks explicitly (`core/` vs `sandbox/`).

---

# Strengths
- Clear and socially relevant educational objective.
- Strong alignment with course requirements (data treatment + three model families + comparison).
- Good experimental decomposition across pipeline phases.
- Presence of intermediate processed artifacts supports analysis continuity.
- Evidence of regularization/validation thinking (e.g., CV for tree and SVM tuning, Ein/Eout discussion).

# Weaknesses
- Reproducibility relies on implicit environment assumptions.
- Raw input dependency mismatch (`data/raw` absent in snapshot).
- Canonical execution path is not centralized.
- Notebook-heavy structure includes side branches and practice notebooks that dilute navigation clarity.

# Risks or Gaps
- **Reconstruction risk:** Future users may not reproduce upstream preprocessing exactly.
- **Interpretation risk:** Model-comparison conclusions may be hard to audit without standardized experiment log schema.
- **Maintenance risk:** Drift between final report notebook and model-specific notebooks can create conflicting narratives.
- **Data access risk:** Source access setup (billing/project/env) is not fully operationalized in top-level docs.

# Suggested Next Steps
1. Add `requirements.txt` (or `environment.yml`) with tested versions.
2. Create a concise reproducibility guide in README (`setup`, `data`, `run-order`, `expected artifacts`).
3. Define one canonical notebook or script as the official final pipeline and label others as exploratory.
4. Add a small metadata file describing each dataset artifact (`origin`, `shape`, `target definition`, `date`).
5. Record key metric tables in a stable markdown/CSV summary to decouple conclusions from notebook output cells.

# Potential Future Directions
- Extend to multiclass calibrated analysis while preserving binary comparison baseline.
- Add temporal/generalization analysis by training on subsets of years and testing on held-out years.
- Evaluate fairness and subgroup robustness across non-protected educational strata (while respecting project scope).
- Compare additional interpretable models (e.g., calibrated logistic/gradient boosting with SHAP summaries).
- Convert notebook pipeline into modular scripts for repeatable academic replication.

---

# Appendix

## Notable Files
- `README.md`
- `AM_Projeto_Erlon_Lacerda_Maria_Bandeira-v2.ipynb`
- `treatment_analysis/1_initial-treatment.ipynb`
- `treatment_analysis/2_columns-treatment.ipynb`
- `treatment_analysis/3_correlation_featureengineering.ipynb`
- `treatment_analysis/4_data-analysis.ipynb`
- `treatment_analysis/5_data-interpos.ipynb`
- `data-gathering/download_data.ipynb`
- `docs/Projeto_Final_da_disciplina.pdf`

## Datasets and Artifacts Observed
- `data/saeb_pb_2017-2007_treated.csv` (observed via shell: 232,882 rows, 51 columns)
- `data/saeb_pb_2017-2007_cleaned.pkl`
- `data/saeb_pb_2017-2007_fe.pkl`
- `data/saeb_pb_2017-2007_fe_balanced.pkl`
- `data/random_rows/*.json` (sample trace artifacts)

## Important Modules / Experimental Areas
- Data acquisition and SQL extraction: `data-gathering/`
- Core preprocessing and feature engineering: `treatment_analysis/`
- Model experiments and comparisons: `models/` + final integrated notebook

## Experiment Observations (from recorded notebook outputs)
- Final integrated notebook reports approximate test accuracies:
  - ANN: ~0.88
  - Decision Tree (pruned): ~0.90
  - SVM: ~0.87
- Reported decision-tree pruning search includes best alpha around `0.0010465` (as printed in notebook output).
- Balancing notebook indicates binary restructuring with equalized class counts in one processed stage.

## Inferred Architecture
A notebook-centric research pipeline with data lifecycle:
`Raw acquisition -> Harmonization/cleaning -> Semantic encoding -> Feature selection -> Class restructuring/balancing -> Model training/evaluation`.

## Assumptions vs Confirmed Findings
- **Confirmed:** Course-project framing and evaluation criteria from `docs/Projeto_Final_da_disciplina.pdf`.
- **Confirmed:** Mission statement and treatment ordering from README/final notebook markdown.
- **Confirmed:** Multi-model implementation and printed metrics from final notebook outputs.
- **Confirmed:** Processed data artifacts exist in `data/`; `data/raw` folder absent in current snapshot.
- **Inferred (medium confidence):** Primary long-term use beyond grading includes portfolio/continuation value.
- **Inferred (medium confidence):** Re-running exact historical results may vary due to unpinned dependencies.

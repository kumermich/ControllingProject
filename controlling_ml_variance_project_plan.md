# Controlling + Analytics (Python) Portfolio Project

## Project Title
**Explain the Variance**: Standard Cost Variance Analysis + ML Driver Attribution (Python)

## Objective
Build an end-to-end controlling project that:
- Computes classic standard cost variances (materials, labor, overhead)
- Identifies material drivers behind unfavorable/favorable variances
- Uses interpretable ML models to attribute variance movements to operational factors
- Produces a portfolio-ready narrative, visuals, and reproducible code

## Assumptions and Scope
- A fictional (synthetic) manufacturing dataset is generated to avoid confidentiality issues
- Monthly data for 12–24 months, plus operational drivers (e.g., downtime, overtime rate, scrap rate)
- Focus on interpretability and managerial actionability over complex modeling

---

# Phase 0 — Setup and Governance

## Task 0.1: Define business context and storyline
- Pick a simple, realistic manufacturing setting (e.g., single plant, 2–3 products)
- Define planning cadence (monthly) and what “standard” means (frozen at budget)
- Define decision questions the controller answers:
  - Which variances matter most?
  - What operational factors explain them?
  - What actions should management take?

## Task 0.2: Define deliverables
- A reproducible Python project structure
- A single notebook (or scripts + notebook) that runs end-to-end
- A concise write-up suitable for portfolio (markdown + exported PDF optional)

## Task 0.3: Create repo structure (local)
- `data/` (generated synthetic data)
- `notebooks/` (analysis notebook)
- `src/` (variance calculations, feature engineering, modeling utilities)
- `reports/` (exported figures and final summary markdown)

Acceptance criteria
- Clear project narrative and scoped dataset design
- Project folders and placeholders created

---

# Phase 1 — Data Design (Synthetic Dataset)

## Task 1.1: Define entities and grain
- Grain: product × month (and optionally plant × product × month)
- Entities:
  - Products: A, B (optionally C)
  - Time: 18 months (suggested)

## Task 1.2: Define standards and actuals
For each product-month:
- Standard quantities and prices (materials, labor hours, overhead rates)
- Actual quantities and prices
- Volume/activity measures (units produced, machine hours)

## Task 1.3: Define operational drivers (features)
Examples (choose 6–10):
- Overtime rate
- Absenteeism rate
- Supplier switch flag
- Scrap rate
- Rework hours
- Machine downtime hours
- Batch size / number of setups
- Rush orders share
- Inflation index proxy

## Task 1.4: Generate synthetic data with controlled relationships
- Create realistic correlations:
  - Higher downtime increases labor inefficiency
  - Supplier switch increases material price variance temporarily
  - Higher scrap rate increases material quantity variance
  - Higher overtime increases labor rate variance

Acceptance criteria
- Dataset saved as CSV(s) under `data/`
- Data dictionary documented (column definitions and units)

---

# Phase 2 — Controlling Core: Standard Variance Calculations

## Task 2.1: Implement variance formulas
At minimum:
- Materials:
  - Price variance
  - Quantity (usage) variance
- Labor:
  - Rate variance
  - Efficiency variance
- Overhead (choose one approach and be explicit):
  - Variable overhead spending and efficiency (optional)
  - Fixed overhead spending and volume (optional)

## Task 2.2: Validate calculations with test cases
- Create 2–3 hand-check scenarios to validate formulas
- Add automated checks (assertions) where possible

## Task 2.3: Create variance summary tables
- By month
- By product
- Top-N unfavorable variances

Acceptance criteria
- Variance outputs reconcile (total variance equals price+quantity, etc.)
- Tables are reproducible from raw synthetic data

---

# Phase 3 — Analytics Layer: Driver Attribution Modeling

## Task 3.1: Choose target(s)
Pick 1–3 targets to model (start with one):
- Material quantity variance (currency)
- Labor efficiency variance (currency)
- Overhead spending variance (currency)

## Task 3.2: Feature engineering
- Lags (e.g., downtime last month)
- Rolling means (3-month rolling scrap)
- Interaction features if needed (overtime × downtime)
- One-hot encoding for product

## Task 3.3: Train/test split strategy
- Time-based split (train on early months, test on later months)
- Avoid leakage (do not use future info)

## Task 3.4: Model selection (interpretable first)
Compare 2–3 models:
- Linear regression / Ridge
- Decision tree
- Random forest or gradient boosting (only if you keep explanation clear)

## Task 3.5: Explainability and attribution
- Feature importance (tree-based)
- Coefficients (linear)
- Optional: SHAP values if available and easy to explain

## Task 3.6: Evaluate performance
- MAE / RMSE
- Directional accuracy (sign of variance)
- Stability checks across products

Acceptance criteria
- Model produces credible attribution aligned with the synthetic causal design
- Clear narrative: top drivers and how they map to controllable actions

---

# Phase 4 — Visualization and Controller-Ready Story

## Task 4.1: Core visuals (must-have)
- Variance trend lines (monthly)
- Variance waterfall for a selected month (bridge budget to actual)
- Driver importance chart

## Task 4.2: Diagnostics (nice-to-have)
- Residual plots
- Predicted vs actual variance scatter
- Segment views by product

## Task 4.3: Management insights write-up
For each key variance:
- What happened (magnitude, timing, products)
- Why it happened (top drivers)
- What to do (actions, owners, timeline)
- What to monitor (KPIs and thresholds)

Acceptance criteria
- Plots are consistent, labeled, and readable
- Narrative reads like a controller’s commentary, not a data science report

---

# Phase 5 — Portfolio Packaging

## Task 5.1: Create a README (project overview)
Include:
- Business problem
- Dataset description (synthetic)
- Methods (variance formulas + model)
- Key results (bullets)
- How to run

## Task 5.2: Create a concise portfolio page (markdown)
Suggested sections:
- Context
- Approach
- Results
- What I would do next in a real company

## Task 5.3: Optional exports
- Export key figures into `reports/`
- Export markdown to PDF (optional, if you want)

Acceptance criteria
- A recruiter can understand value in under 2 minutes
- Code runs end-to-end without manual steps

---

# Phase 6 — Extensions (Optional, Strong Differentiators)

## Extension A: Rolling forecast integration
- Use a simple forecasting model to predict drivers (scrap, downtime)
- Propagate into expected variances

## Extension B: Early-warning system
- Flag months likely to exceed variance thresholds
- Evaluate precision/recall for alerts

## Extension C: Control design
- Propose KPI redesign and governance rules
- Tie back to incentive alignment and organizational architecture

---

# Milestone Plan (Suggested Timeline)

## Milestone 1 (Day 1)
- Phase 0 complete
- Synthetic dataset generated + documented

## Milestone 2 (Day 2)
- Variance calculations implemented and validated
- Summary tables created

## Milestone 3 (Day 3)
- One variance modeled with interpretable ML
- Driver attribution and evaluation done

## Milestone 4 (Day 4)
- Visuals + management narrative complete
- Portfolio markdown + README finalized

---

# Definition of Done (DoD)
- Reproducible run from raw synthetic data to final figures
- Variance calculations correct and explained
- ML component interpretable and clearly connected to operational actions
- Final markdown write-up suitable for portfolio

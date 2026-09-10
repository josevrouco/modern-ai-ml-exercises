# Exercise 01 — HomeValue: Pricing Homes for Acquisition

[![Open starter in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/lathrahul/modern-ai-ml-exercises/blob/main/exercise-01-homevalue/notebooks/getting_started.ipynb) [![Explore outputs in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/lathrahul/modern-ai-ml-exercises/blob/main/shared/explore_outputs_in_colab.ipynb)

**Release:** End of Session 1  
**Due:** Sunday, September 20, 2026 at 11:59 PM ET  
**Expected effort:** 5–7 hours  
**Work mode:** Individual

## How the starter notebook fits

The Colab starter is both the **Week 2 guided clinic** and the starting workspace for Exercise 01. During class, complete Sections 1–8 to compare prepared baselines and regression models, inspect residual evidence, and make an initial model decision. Section 9 marks the transition to your independent exercise work.

The guided clinic is not the complete submission. After class, use the full requirements below to extend the analysis, generate predictions for the test properties, write the acquisition memo, and prepare the required files for Blackboard.

### In-class coefficient memo

Before leaving the Week 2 clinic, save four bullets in your notebook:

1. the acquisition decision the model can support;
2. one coefficient interpreted with units and conditional language;
3. held-out evidence compared with the baseline; and
4. one limitation, operating guardrail, or next test.

This is a working checkpoint, not a separate submission. Revise these bullets into the one-page acquisition memo required for the final Exercise 01 submission.

## Start and submit

1. Open the starter notebook with the Colab button above and select **File → Save a copy in Drive**. Do not use a GitHub Gist.
2. During the Week 2 clinic, complete Sections 1–8 and save your initial decision, evidence, and unresolved risk.
3. After class, continue from Section 9 and complete every requirement in this brief. Restart the runtime and run the finished notebook from top to bottom.
4. Validate `submission.csv`, then inspect it with the [shared output explorer](../shared/OUTPUT_EXPLORER.md).
5. Download the executed notebook and required outputs to your computer.
6. Assemble the files using the [submission guidelines](../shared/submission_guidelines.md) and submit them through the Exercise 01 assignment in Blackboard. Blackboard is the source of truth for the due date and submission field.

Nothing is due for Exercise 01 before the Monday, September 14 class. Bring only the saved clinic checkpoint and one unresolved question to that session.

## Your role

You are a junior data scientist at Northstar Residential, a property investment firm. Acquisition analysts review hundreds of properties and need a defensible screening value before commissioning a full appraisal. Overpaying destroys returns; rejecting every uncertain property leaves good opportunities undiscovered.

Build a model that estimates a home's inflation-normalized sale price from facts available during initial screening. Your work will be used for **triage**, not as a substitute for a licensed appraisal.

## Business questions

1. How accurately can a simple, explainable model estimate value?
2. Which property characteristics have the clearest relationship with value?
3. For which homes is the model least reliable?
4. Is the model good enough for preliminary screening, and under what guardrails?

## Data

- `data/train.csv`: historical properties with `sale_price`.
- `data/test.csv`: later-period properties without the target.
- `data/data_dictionary.md`: field definitions and important caveats.
- `sample_submission.csv`: required prediction schema.

The records derive from Ames Housing data. Identifiers, field names, and the target have been prepared specifically for this course. Missing values may mean either “not recorded” or “feature not present”; investigate before choosing a treatment.

## Required analysis

1. Audit the data and state what one row represents.
2. Establish a median-price baseline.
3. Create a validation strategy and explain why it is appropriate.
4. Fit and interpret at least:
   - a simple linear regression using one numeric feature;
   - a multiple linear regression using numeric and categorical features.
5. Compare validation performance with the baseline.
6. Inspect residuals overall and for at least two meaningful groups.
7. Generate predictions for every test property.

Do not use tree ensembles, boosting, neural networks, external data, or manually recovered public labels. A log transformation is allowed if you explain why it helps.

## Expected outputs

### 1. Prediction file

`submission.csv` with exactly:

```text
property_id,predicted_sale_price
HOME-123456,185000
```

Predictions must be positive, finite dollar amounts. Validate the file with:

```bash
python3 checks/validate_submission.py submission.csv
```

### 2. Executed notebook

Show the baseline, preprocessing, validation, model comparison, residual analysis, and final prediction process. The notebook must run from top to bottom without manual edits.

### 3. One-page acquisition memo

Write for the Director of Acquisitions. Include the recommended use of the model, validation evidence in dollars and percentages, three valuation relationships, the model's weakest segment, and two operating guardrails.

## Technical evaluation metric

Predictions are scored using **root mean squared logarithmic error (RMSLE)**. This emphasizes proportional error and reduces domination by a few expensive homes. Lower is better.

There is no public course leaderboard. The instructor evaluates submitted predictions against withheld outcomes after the deadline; those labels are never provided to students.

## Success criterion

A technically credible submission beats the median baseline and explains where it should not be trusted. Predictive performance cannot compensate for leakage or an irreproducible notebook.

## Data source

[Ames Housing](https://cmustatistics.github.io/data-repository/money/ames-housing.html), compiled by Dean De Cock from Ames City Assessor's Office records.

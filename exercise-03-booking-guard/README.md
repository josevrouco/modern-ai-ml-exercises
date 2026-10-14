# Exercise 03 — BookingGuard: Protecting Hotel Revenue

[![Open starter in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/lathrahul/modern-ai-ml-exercises/blob/main/exercise-03-booking-guard/notebooks/getting_started.ipynb) [![Explore outputs in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/lathrahul/modern-ai-ml-exercises/blob/main/shared/explore_outputs_in_colab.ipynb)

**Release:** Session 7  
**Due:** See the Blackboard Due Date field. The two-week no-class period after Session 7 changes the ordinary weekly cadence, so do not infer a date from “before Session 8.”
**Expected effort:** 5–7 hours  
**Work mode:** Individual

## Start and submit

1. Open the starter notebook with the Colab button above and select **File → Save a copy in Drive**. Do not use a GitHub Gist.
2. Complete the analysis and maintain the required experiment table inside the notebook or as a CSV.
3. Restart the runtime, run every cell, validate `submission.csv`, and inspect it with the [shared output explorer](../shared/OUTPUT_EXPLORER.md).
4. Download the executed notebook and required outputs to your computer.
5. Assemble the files using the [submission guidelines](../shared/submission_guidelines.md) and submit them through the Exercise 03 assignment in Blackboard. Blackboard is the source of truth for the due date and submission field.

## Week 7 classroom boundary

In class, read the brief, define the prediction moment, identify likely leakage, inspect the submission contract, and write the first experiment hypothesis. The separate [Week 7 boosting lab](../shared/WEEK_07_BOOSTING_LAB.md) starts and ends in class. It does not complete any part of this take-home exercise.

After class, independently run the BookingGuard notebook and complete the model benchmarks, five-run experiment record, calibration and threshold analysis, sensitivity to every supplied policy assumption, analysis across at least three operational groups, final model and threshold decision, memo, and validated submission file. The starter does not prefill a winning model, threshold, or recommendation.

## Your role

You support revenue management for a hotel group. Late cancellations leave rooms empty, but requiring a deposit from every guest creates friction and reduces bookings. At a fixed decision point before arrival, predict cancellation risk and recommend which bookings should require a deposit.

## Business questions

1. Which bookings are most likely to cancel?
2. Does gradient boosting materially improve on logistic regression and Random Forest?
3. Which probability threshold produces the strongest expected policy value?
4. Where does the policy fail across hotel, market, and customer groups?

## Data

- `data/train.csv`: arrivals before July 2017, including `canceled`.
- `data/test.csv`: July–August 2017 arrivals without labels.
- `data/policy_costs.csv`: published decision assumptions.
- `data/data_dictionary.md`: prediction-time field definitions.
- `sample_submission.csv`: required schema.

The holdout is later in time. Random cross-validation alone may overstate performance when demand patterns shift.

## Required analysis

1. Define the prediction moment and audit leakage.
2. Establish prevalence and logistic-regression baselines.
3. Use a time-aware validation design.
4. Compare logistic regression, Random Forest, and one gradient-boosting implementation.
5. Track at least five deliberate experiments in a documented table, including parameters, validation period, runtime, and metrics.
6. Evaluate log loss, PR-AUC, ROC-AUC, calibration, and policy value.
7. Select a deposit threshold and test its sensitivity to all supplied cost assumptions.
8. Analyze error or policy rates across at least three operational groups.

Do not use reservation status, post-arrival information, external labels, or reconstructed source outcomes.

## Expected outputs

### Prediction and policy file

```text
booking_id,cancellation_probability,require_deposit
BOOK-123456,0.71,1
```

Validate it with:

```bash
python3 checks/validate_submission.py submission.csv
```

### Notebook and experiment report

Provide an executed, reproducible notebook plus the required experiment table in the notebook or as a CSV.

### Revenue-management memo

In one page, recommend a threshold, expected deposits per 1,000 bookings, expected value, evidence of temporal generalization, important drivers, and two guest-experience guardrails.

## Technical evaluation

The predictive component uses log loss. The policy component applies the published economics to withheld outcomes after the deadline. There is no public course leaderboard.

## Source

[Hotel Booking Demand datasets](https://doi.org/10.1016/j.dib.2018.11.126) by António, de Almeida, and Nunes, CC BY 4.0.

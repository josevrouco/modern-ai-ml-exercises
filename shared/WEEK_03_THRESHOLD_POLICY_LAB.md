# Week 3 Threshold Policy Lab

[![Open in Google Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/lathrahul/modern-ai-ml-exercises/blob/main/shared/notebooks/week_03_threshold_policy_lab.ipynb)

## Purpose

The model has already produced fraud probabilities. Your task is to choose an operating policy that fits a daily capacity of 400 reviews.

This is a 20-minute, ungraded pair activity. There is no separate notebook upload. Use one result as evidence in the Week 3 Participation Card.

## Pair roles

- **Driver:** Opens Colab and runs the notebook cells.
- **Navigator:** Records how workload, false positives, false negatives, precision, recall, and expected cost change.
- Switch roles after the first threshold results table.

## Activity

1. Predict how the metrics will change before running the threshold comparison.
2. Compare fixed thresholds with top-150, top-400, and top-1,200 policies.
3. Exclude policies that exceed the 400-review capacity.
4. Change one cost assumption and check whether your preferred policy changes.

## Participation-card handoff

Record six items before closing the notebook:

1. A feasible threshold, top-k, or escalation policy.
2. One supporting count or rate.
3. The error your policy most needs to avoid and why.
4. The workload or escalation limit your policy must respect.
5. One change in cost, capacity, prevalence, or calibration that could change your recommendation.
6. One missing fact, subgroup check, or validation result you would request before deployment.

The probabilities and cost assumptions are illustrative. Do not interpret the notebook as a deployed fraud system.

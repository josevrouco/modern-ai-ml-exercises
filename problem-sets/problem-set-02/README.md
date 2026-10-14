# Problem Set 02 - Classification Decisions and Regularization

**Weight:** 3%  
**Work mode:** Individual  
**Suggested time:** 45-60 minutes  
**AI level:** Yellow - assistance permitted with disclosure

## Case

HarborBank uses a classifier to identify customers who may miss their next loan
payment. A flagged customer receives a support call. Each call costs $12. An
unflagged customer who misses a payment creates an estimated $180 loss. The
validation set contains 1,000 customers, including 100 who miss a payment. The
support team can place **at most 150 calls** during this decision period.

| Threshold | Precision | Recall | Flagged customers | Missed positive cases |
|---:|---:|---:|---:|---:|
| 0.30 | 0.32 | 0.88 | 275 | 12 |
| 0.50 | 0.50 | 0.70 | 140 | 30 |
| 0.70 | 0.68 | 0.41 | 60 | 59 |

Two logistic-regression models were fit using the same rows, features,
preprocessing pipeline, and five validation folds:

| Model | Training AUC | Mean five-fold validation AUC | Nonzero coefficients |
|---|---:|---:|---:|
| Near-unpenalized logistic regression | 0.91 | 0.74 | 84 |
| Cross-validated Lasso logistic regression | 0.82 | 0.79 | 26 |

## Questions

### 1. Define the prediction decision - 0.35 points

State the unit of analysis, target, prediction moment, and operational action.

### 2. Compute expected operating cost - 0.55 points

For each threshold, calculate `12 × flagged customers + 180 × missed positive
cases`. Show your work and identify the lowest-cost threshold.

### 3. Explain the threshold tradeoff - 0.35 points

Why does raising the threshold generally increase precision while decreasing
recall? Explain in business terms, not only metric definitions.

### 4. Recommend a threshold - 0.45 points

Apply the 150-call capacity limit. Which listed threshold is feasible and has
the lowest expected cost? State one nonfinancial consideration that could still
change the operating decision.

### 5. Diagnose regularization - 0.40 points

Which logistic-regression model currently has stronger generalization evidence?
Use the train-validation gap, mean validation AUC, and coefficient counts. Why
does this evidence support a candidate rather than prove a final winner?

### 6. Recognize a nonlinear effect - 0.25 points

Suppose the observed missed-payment rate falls sharply during the first 12
months of customer tenure and then levels off. Explain why one linear tenure
term may underfit this pattern. Name one candidate extension discussed in class
and one validation result you would inspect before keeping it.

### 7. Check subgroup performance - 0.30 points

Suppose recall at threshold 0.50 is 0.78 for long-tenure customers and 0.46 for
new customers. Give one diagnostic and one possible operating response.

### 8. Final recommendation - 0.35 points

Suppose the estimated loss from a missed positive case falls from $180 to $60.
Recalculate expected cost for all three thresholds. In 100-150 words, recommend
a model-and-threshold policy that accounts for capacity and this sensitivity
result, then name one monitoring metric to review after launch.

## Submission

Enter all eight numbered responses directly in Blackboard. Include this final
statement:

- If AI was used: name the system, purpose, prompts or prompt log, how output
  was used, and how you verified it.
- If AI was not used: `No generative AI tools were used in preparing this submission.`

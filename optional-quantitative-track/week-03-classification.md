# Week 3 — Optional Quantitative Extension

Estimated time: **60–120 minutes**, depending on the route selected.

## Suggested reading

- Prince, *Understanding Deep Learning*, Sections 5.1, 5.2, 5.4, and 5.7.
- ISLP, Chapter 4 and the Python lab.
- For more formal treatment, *The Elements of Statistical Learning*, selected Chapter 4 sections.

## Exercise A — From score to probability and odds

For logistic scores `z = -2, 0, 2`:

1. Compute `p = 1 / (1 + exp(-z))`.
2. Compute the odds `p / (1 - p)`.
3. Compute the log odds.
4. Explain why a one-unit change in a predictor does not imply a constant change in probability.

<details>
<summary>Self-check</summary>

The probabilities are approximately `0.1192`, `0.5`, and `0.8808`; the odds are approximately `0.1353`, `1`, and `7.3891`; and the log odds recover `-2`, `0`, and `2`.

</details>

## Exercise B — Why confident errors cost more under log loss

Suppose the observed outcome is `y = 0`. Calculate log loss when the model assigns `p(y=1)` equal to `0.55`, `0.80`, and `0.99`.

<details>
<summary>Self-check</summary>

The losses are `-log(0.45) ≈ 0.799`, `-log(0.20) ≈ 1.609`, and `-log(0.01) ≈ 4.605`. A confident wrong probability receives a much larger penalty.

</details>

## Exercise C — Calibration and policy threshold

Using the Retention training data:

1. Split the data into training and validation sets.
2. Fit logistic regression and generate validation probabilities.
3. Plot a calibration curve.
4. Calculate log loss and Brier score.
5. Compare the default `0.5` threshold with `C_FP / (C_FP + C_FN)`.
6. Report how contacts, false positives, and false negatives change.

<details>
<summary>Self-check</summary>

The threshold is a policy choice layered on top of the fitted probabilities. A lower threshold generally increases contacts and recall while also increasing false positives. The cost formula requires calibrated probabilities, fixed costs, a binary decision, and no binding capacity constraint.

</details>

## Exercise D — Threshold sensitivity

Hold the false-positive cost fixed at `$12` and calculate the simple threshold when the false-negative cost is `$60`, `$180`, and `$300`.

<details>
<summary>Self-check</summary>

The corresponding thresholds are approximately `0.1667`, `0.0625`, and `0.0385`. Higher false-negative cost lowers the action threshold under this simplified decision model.

</details>

## Go deeper

- Gneiting and Raftery (2007), “Strictly Proper Scoring Rules, Prediction, and Estimation.”
- Niculescu-Mizil and Caruana (2005), “Predicting Good Probabilities with Supervised Learning.”
- Charles Elkan (2001), “The Foundations of Cost-Sensitive Learning.”
- Scikit-learn examples on probability calibration and cost-sensitive threshold tuning.


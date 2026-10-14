# Exercise 02 — Save or Let Go: Customer Retention Decisions

[![Open starter in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/lathrahul/modern-ai-ml-exercises/blob/main/exercise-02-retention/notebooks/getting_started.ipynb) [![Explore outputs in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/lathrahul/modern-ai-ml-exercises/blob/main/shared/explore_outputs_in_colab.ipynb)

**Release:** End of Session 4  
**Due:** Wednesday, October 14, 2026 at 11:59 PM EDT (Blackboard controls any announced change)

**Expected effort:** 5–7 hours  
**Work mode:** Individual

## Classroom flow and checkpoints

This starter notebook belongs to the **graded, multiweek Exercise 02**. It is
separate from the shorter in-class guided-practice notebooks.

1. **Week 4 checkpoint:** inspect relationships; fit Model A with tenure, Model B with tenure and monthly charges, and Model C with the full feature set; evaluate the baseline with a stratified split and five-fold cross-validation. Before regularization, distinguish these modeling iterations from the optimizer iterations used to fit one fixed specification.
2. **Week 5 checkpoint A:** redo Model C with near-unpenalized, Ridge, and Lasso logistic regression while keeping rows, preprocessing, folds, and metrics fixed.
3. **Week 5 checkpoint B:** convert probabilities into a retention-contact policy using campaign economics, contact capacity, and one sensitivity scenario.
4. **Week 6 in class:** compare a quadratic polynomial, a selected spline, and a GAM-style additive logistic model before moving to trees. Carry one nonlinear candidate into the tree and Random Forest comparison. The class hard stop is after Section 7, permutation importance.
5. **Week 6 independent completion:** run one controlled tree robustness experiment, choose the final model and threshold, produce a confusion matrix at that threshold, test the final model under the lower-margin scenario, choose one additional diagnostic, and write the final recommendation before generating the decision file.

The Week 5 checkpoint should be complete before adding the Week 6 comparison. The starter notebook now compares a quadratic tenure model, three declared spline configurations, and a GAM-style additive logistic model with smooth tenure and monthly-charge effects. It carries one selected nonlinear candidate into a fair comparison with regularized logistic regression, a shallow classification tree, and a Random Forest. It also includes threshold-policy comparisons, a subgroup check, permutation importance, required robustness and sensitivity work, and a student-owned final recommendation.

### Week 6 classroom run

From a fresh Colab runtime, select the first Week 6 code cell and use **Runtime -> Run before** to rebuild the prerequisites. Then run Sections 0-7 with the class, one section at a time. Do **not** use **Run all** during class: Sections 8-11 intentionally wait for your decisions.

## Start and submit

1. Open the starter notebook with the Colab button above and select **File → Save a copy in Drive**. Do not use a GitHub Gist.
2. Complete the analysis, restart the runtime, and run every cell from top to bottom.
3. Validate `submission.csv`, then inspect it with the [shared output explorer](../shared/OUTPUT_EXPLORER.md).
4. Download the executed notebook and required outputs to your computer.
5. Assemble the files using the [submission guidelines](../shared/submission_guidelines.md) and submit them through the Exercise 02 assignment in Blackboard. Blackboard is the source of truth for the due date and submission field.

## Your role

You are a data scientist supporting the retention team at Meridian Telecom. The team can contact only a fraction of customers. Every contact costs money, accepted offers reduce margin, and contacting customers who would stay anyway wastes budget.

Build a model that estimates each customer's churn probability, then translate those probabilities into a contact decision. The goal is not merely to identify churners—it is to create a defensible retention policy.

## Business questions

1. Who is most likely to churn?
2. At what probability threshold should the team intervene?
3. What is the estimated financial value of the policy?
4. How sensitive is the decision to uncertain campaign assumptions?

## Data

- `data/train.csv`: customer attributes and observed `churned` outcome.
- `data/test.csv`: customers requiring probabilities and decisions.
- `data/campaign_costs.csv`: supplied decision assumptions.
- `data/data_dictionary.md`: field definitions.
- `sample_submission.csv`: required schema.

The data derive from IBM's fictional telecom sample and have been prepared specifically for the course.

## Required analysis

1. Audit prevalence, missingness, and the unit of analysis.
2. Establish an always-stay baseline.
3. Use stratified cross-validation or justify a stronger alternative.
4. Fit and compare:
   - near-unpenalized logistic regression;
   - Ridge (L2) logistic regression;
   - Lasso (L1) logistic regression;
   - a quadratic, spline, and GAM-style nonlinear checkpoint;
   - a shallow decision tree and a Random Forest after Session 6, using the same validation design for comparison.
5. Report ROC-AUC, PR-AUC, log loss, and at least one confusion matrix.
6. Calculate expected campaign value over a range of thresholds using the supplied assumptions.
7. Select one threshold and perform a sensitivity analysis.
8. Generate a probability and contact decision for every test customer.

Do not use boosting, neural networks, external customer data, or reconstructed public labels.

## Expected outputs

### 1. Decision file

`submission.csv` with exactly:

```text
customer_id,churn_probability,contact_customer
CUST-123456,0.73,1
```

`contact_customer` must be `0` or `1`. Validate with:

```bash
python3 checks/validate_submission.py submission.csv
```

### 2. Fully executed notebook

Show preprocessing, cross-validation, model comparison, probability evaluation, threshold economics, sensitivity analysis, and final decision generation, with visible outputs and the AI-use disclosure inside the notebook.

### 3. One-page retention memo

Write for the VP of Customer Retention. Recommend a policy, expected contacts per 10,000 customers, expected value under the supplied assumptions, key churn signals, sensitivity risks, and one fairness or customer-experience concern.

### 4. Methodology deck

Submit a concise deck in **PPTX or PDF**. Three slides are recommended: validation and model choice; threshold and economics; recommendation and limitation. The deck summarizes evidence already present in the notebook and memo. **No video recording is required.**

## Technical evaluation

The technical component uses **log loss**, rewarding useful probabilities rather than only rankings. The decision component evaluates realized campaign value using the submitted `contact_customer` policy and withheld outcomes after the deadline. There is no public course leaderboard.

## Data source

[IBM Telco Customer Churn sample](https://github.com/IBM/telco-customer-churn-on-icp4d).

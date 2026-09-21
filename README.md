# Modern AI & Machine Learning — Applied Challenges

Six business-facing machine-learning exercises spanning the full course sequence. Each challenge is designed for approximately 5–7 hours of student work over a 7–10 day window.

## Individual problem sets

The five short individual problem sets are available in the
[problem-sets directory](problem-sets/). Submit responses in Blackboard; GitHub
hosts the formatted briefs only.

[![Open output explorer in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/lathrahul/modern-ai-ml-exercises/blob/main/shared/explore_outputs_in_colab.ipynb)

## Shared in-class tools

- [Week 3 Threshold Policy Lab](shared/WEEK_03_THRESHOLD_POLICY_LAB.md) — an ungraded pair activity comparing thresholds and top-k policies under cost and review-capacity constraints.

| Exercise | Course sessions | Core question | Primary method |
|---|---:|---|---|
| [First Flight](exercise-00-tooling-warmup/) | Session 1 | Can I complete the GitHub–Colab submission workflow? | Tooling rehearsal |
| [HomeValue](exercise-01-homevalue/) | 1–3 | What is a defensible screening value for a home? | Linear regression |
| [Save or Let Go](exercise-02-retention/) | 4–6 | Which customers should receive a retention offer? | Classification and thresholding |
| [BookingGuard](exercise-03-booking-guard/) | 7–8 | Which hotel bookings warrant a deposit? | Gradient boosting and model selection |
| [Segment Studio](exercise-04-segment-studio/) | 9–10 | Which customer segments deserve distinct strategies? | Clustering, PCA, and business storytelling |
| [VisualSort](exercise-05-visual-sort/) | 11–13 | Can transfer learning route retail images reliably? | Neural networks and transfer learning |
| [Causal Campaign](exercise-06-causal-campaign/) | 14 | Did the email campaign cause incremental purchases? | Causal inference and responsible AI |

## Submission principles

- Start with a simple baseline and improve it deliberately.
- Use a pipeline so preprocessing learned from training data is not leaked into validation.
- Evaluate the model in technical and business terms.
- Submit reproducible work: Restart the runtime and run all cells before submission.
- Disclose use of generative AI using [the course template](shared/ai_use_disclosure.md).

The test labels and instructor solutions are intentionally absent from this repository.

## Environment

Google Colab is recommended. For local use, install the packages in `requirements.txt` with Python 3.10 or later.

- Start with [Exercise 00: First Flight](exercise-00-tooling-warmup/).
- Use the [shared Colab output explorer](shared/OUTPUT_EXPLORER.md) to inspect any challenge submission.

## Data provenance

- Exercise 1 derives from the Ames Housing data made available by Dean De Cock and the Ames City Assessor's Office: https://cmustatistics.github.io/data-repository/money/ames-housing.html
- Exercise 2 derives from IBM's fictional Telco Customer Churn sample: https://github.com/IBM/telco-customer-churn-on-icp4d
- Exercise 3 derives from the Hotel Booking Demand datasets: https://doi.org/10.1016/j.dib.2018.11.126
- Exercise 4 derives from UCI Online Retail: https://doi.org/10.24432/C5BW33
- Exercise 5 derives from Fashion-MNIST: https://github.com/zalandoresearch/fashion-mnist
- Exercise 6 derives from Kevin Hillstrom's email marketing challenge: https://blog.minethatdata.com/2008/03/minethatdata-e-mail-analytics-and-data.html

The challenge datasets use randomized identifiers and course-specific preparation where appropriate. Do not attempt to reconstruct labels from online copies.

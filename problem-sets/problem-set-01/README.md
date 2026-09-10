# Problem Set 01 - Framing, Baselines, and Regression Evidence

**Weight:** 3%  
**Work mode:** Individual  
**Due:** Thursday, September 17, 2026 at 11:59 PM ET  
**Suggested time:** 45-60 minutes  
**AI level:** Yellow - assistance permitted with disclosure

## How this fits Week 2

This problem set checks individual reasoning about framing, baselines, validation, coefficients, and regression watchouts. It uses the same Northstar Residential context as HomeValue, but it is a separate Blackboard submission and does not require completion of the HomeValue notebook.

The set is launched at the end of Week 2 and is **not** preparation due before the Monday, September 14 class. Complete it after the Week 3 session and submit the eight responses by the deadline above.

## Case

Northstar Residential screens homes before deciding whether to commission a
full appraisal. At the screening moment, the team knows property size, age,
neighborhood, and prior transaction information. A licensed appraisal occurs
only after a property passes screening.

The team compares three approaches on the same untouched validation homes:

| Approach | Training MAE | Validation MAE | Validation RMSE |
|---|---:|---:|---:|
| Median-price baseline | $31,000 | $32,000 | $51,000 |
| Linear regression | $24,000 | $27,000 | $49,000 |
| Highly flexible model | $8,000 | $35,000 | $58,000 |

For the linear model:

- The coefficient on living area is `$92 per square foot`, holding the included
  neighborhood and age variables fixed.
- Validation MAE is `$22,000` for urban homes and `$48,000` for rural homes.
- One 9,500-square-foot property lies far outside the size range of nearly all
  training homes, but its residual is small.

## Questions

### 1. Frame the decision - 0.40 points

State the unit of analysis, prediction target, prediction moment, and business
action this model is intended to support.

### 2. Identify leakage - 0.40 points

Would the licensed appraisal value be an acceptable model input? Answer yes or
no and justify your answer using the prediction moment.

### 3. Choose a model - 0.40 points

Which of the three approaches is the strongest current deployment candidate?
Cite at least two pieces of evidence from the table.

### 4. Explain the generalization gap - 0.35 points

Why is the highly flexible model's low training MAE not sufficient evidence
that it should be deployed?

### 5. Interpret the coefficient - 0.40 points

Write one statistically safe interpretation of the `$92` living-area
coefficient. Then state one reason it should not be interpreted as a causal
effect of adding square footage.

### 6. Diagnose subgroup risk - 0.35 points

What does the urban-versus-rural validation result imply for use of the model?
Give one operating guardrail or next diagnostic.

### 7. Distinguish leverage from residual error - 0.25 points

How should the 9,500-square-foot property be described: outlier, high leverage,
both, or neither? Explain briefly and state what you would do next.

### 8. Make the decision recommendation - 0.45 points

In 100-150 words, recommend whether and how Northstar should use the linear
model. Your response must reference the baseline, validation evidence, rural
performance, and at least one guardrail.

## Submission

Enter all eight numbered responses directly in Blackboard. Include this final
statement:

- If AI was used: name the system, purpose, prompts or prompt log, how output
  was used, and how you verified it.
- If AI was not used: `No generative AI tools were used in preparing this submission.`

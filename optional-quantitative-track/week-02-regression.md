# Week 2 — Optional Quantitative Extension

Estimated time: **60–120 minutes**, depending on the route selected.

## Suggested reading

- Prince, *Understanding Deep Learning*, Chapter 2 and Sections 5.1–5.3.
- ISLP, Chapter 3 and the Python lab.
- For a deeper derivation, *The Elements of Statistical Learning*, selected Chapter 3 sections.

## Exercise A — OLS from first principles

For the points `(x, y) = (1, 2), (2, 3), (3, 5)`:

1. Write the model `ŷᵢ = β₀ + β₁xᵢ`.
2. Write the sum of squared residuals.
3. Differentiate with respect to `β₀` and `β₁`.
4. Solve the two normal equations.
5. Verify the coefficients with `numpy.linalg.lstsq` or `sklearn.linear_model.LinearRegression`.

<details>
<summary>Self-check</summary>

The fitted slope is `1.5`, the intercept is approximately `0.3333`, and the residuals sum to zero. With an intercept included, the residuals are also orthogonal to `x` up to numerical precision.

</details>

## Exercise B — Heteroskedasticity and robust uncertainty

Generate data from:

```python
rng = np.random.default_rng(42)
x = rng.uniform(0, 10, 500)
error = rng.normal(0, 0.5 + 0.4 * x)
y = 5 + 2 * x + error
```

Then:

1. Fit OLS using `statsmodels`.
2. Plot residuals against fitted values.
3. Compare conventional standard errors with HC3 standard errors.
4. Compare validation RMSE before and after changing the covariance estimator.

<details>
<summary>Self-check</summary>

The residual spread should grow with `x`. Changing to HC3 changes the estimated uncertainty, not the fitted coefficients or predictions; therefore validation RMSE is unchanged.

</details>

## Exercise C — Prediction versus inference in HomeValue

Using the HomeValue training data:

1. Fit a model using `living_area_sqft`, `overall_quality`, and `year_built`.
2. Record validation RMSE and coefficients.
3. Add `bedrooms` and `garage_capacity`.
4. Compare validation performance and coefficient stability.
5. Write two statements: one justified predictive claim and one causal claim the evidence does **not** justify.

<details>
<summary>Self-check</summary>

A feature may improve validation performance while materially changing another coefficient because the predictors share information. Neither model identifies the causal effect of changing a home attribute without a defensible identification strategy.

</details>

## Go deeper

- Halbert White (1980), “A Heteroskedasticity-Consistent Covariance Matrix Estimator and a Direct Test for Heteroskedasticity.”
- Leo Breiman (2001), “Statistical Modeling: The Two Cultures.”
- MIT OpenCourseWare 18.650, regression lectures and problem sets.


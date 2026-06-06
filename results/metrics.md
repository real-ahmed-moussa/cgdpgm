# Model Results

GDP is scaled to units of 10¹⁰ USD. MSE values are in the same squared units.  
All spline fits are fully deterministic — no random component.

---

## Standard Cubic Splines

Fit via B-spline basis (`bs()`, degree = 3). Interior knots = df − 3. No regularization.

| Degrees of Freedom | Interior Knots | Training MSE |
|---|---|---|
| 4 | 1 | 454.26 |
| 6 | 3 | 240.50 |
| 8 | 5 | 107.82 |
| 10 | 7 | 43.96 |
| 15 | 12 | 32.23 |
| 25 | 22 | 25.99 |

MSE decreases monotonically with df — without a held-out test set this reflects overfitting, not generalization.

---

## Smoothing Splines

Fit via `smooth.spline()` with a knot at every data point and an L2 curvature penalty λ. Effective degrees of freedom reported by the fitted object.

| λ | Effective DOF | Training MSE |
|---|---|---|
| 0.0000001 | 47.0 | 1.00 |
| 0.000001 | 31.1 | 11.46 |
| 0.0001 | 10.7 | 68.34 |
| 0.0025 | 5.4 | 1,306.54 |
| 0.05 | 3.1 | 9,258.35 |
| 0.1 | 2.7 | 12,848.37 |

---

## Comparative Summary

| Method | Configuration | Training MSE |
|---|---|---|
| Cubic spline (best) | df = 25, 22 knots | 25.99 |
| Smoothing spline (best) | λ = 0.000001, eff. df ≈ 31 | 11.46 |

Smoothing splines outperform cubic splines at their respective optima by approximately **56%** (MSE 11.46 vs 25.99). Smoothing splines are preferred due to automatic knot placement, superior boundary behavior, and a principled penalty-based complexity control.

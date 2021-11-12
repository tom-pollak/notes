# Supervised Learning

> Train machine using data which is well labelled

1. Predictive model construction
2. PM tested using new data
3. PM used for classifying future or unknown cases

## Regression

### Linear

> Multiple Linear Regression
> $Y = b_0 + b_1X_1 + b_2X_2 + b_3X_3 ...$

### Logistic

> ##### $g(z) = \frac{1}{1+e^{-z}}$

As z goes from $- \infty$ to $+ \infty$, $g(z)$ goes from $0$ to $1$

> $h\emptyset(X) = \emptyset_0 + \emptyset_1X$ where $\emptyset_0$ is 

## Classification

Can be binary or multi class
- Can set a **decision boundary** where the classification changes from true to false

## Odds

Normal odds: P(0.8) = P(0.8) / (1 - P(0.8)) = 4
- Ratio of action happening to not happening

> $o_f \cdot o_a = 1$
> - $o_f:$ odds in favour
> - $o_a:$ odds against

> **Log odds:** $log(o_f)$
> - Forms basis of logistic regression

## Confusion Matrix

|                  | Predicted Class (0) | Predicted Class (1) |       |
| ---------------- | ------------------- | ------------------- | ----- |
| Actual Class (0) | TN                  | FP                  | Total |
| Actual class (1) | FN                  | TP                  | Total |
|                  | Total               | Total               |       |

> $Error = 1 - Accuracy$
> $Accuracy = \frac{TP+TN}{TN+FP+FN+TP}$

**Sensitivity:** (recall or true positive rate) Calculated using positives and false positives
- $\frac{TP}{TP + FN}$
- Best is 1.0, worst 0.0
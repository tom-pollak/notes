---
date created: 2021-11-07 14:04
date updated: 2021-11-08 15:02

---

> Machine Learning: Field of study that gives computers the ability to learn without being explicitly programmed

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
- Can set a **descision boundary** where the classification changes from true to false

# Unsupervised Learning

> Classification not provided
>
> - Develop classification labels automatically

> Seek groups of **clusters**: Data that has similarities that can be characterized

## K-Means Clustering

- Number of clusters need to be known
- Maintains _k cluster means_ — centres
- Objects assigned to the closest centre then means updated
- Terminates when the centres do not change or fixed number of iterations has been conducted

Euclidean distance formula: $dist((x, y), (a, b)) = \sqrt{(x - a)^2 + (y - b)^2}$

### Pros

- Computationally faster if K is small
- Works well for large scale data
- Good at capturing structure of data if clusters have spherical shape

### Cons

- Need to pick K
- Sensitive to outliers
- Can't do complex geometric shape

## Alternatives

- **PAM:** K-means but centre are actual data points
- **Fuzzy C-means:** Data assigned to number of clusters with different degrees
- **Mixture of Gaussian:** Probabilistic approach
- **Search-Based:** K does not need to be defined

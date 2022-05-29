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
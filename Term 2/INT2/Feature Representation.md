---
date created: 2022-02-14 16:50
---

# Feature Representation

## Transforming Data

$\varphi: \mathbb{R}^d \rightarrow \mathbb{R}^D$

- $\theta = [\theta_1, \ldots, \theta_d]; \theta_0$
- Originally: $h(x; \theta; \theta_0) = sign(\theta^Tx + \theta_0)$

$\varphi: ([x_1, \ldots, x_d]) = [x_1, \ldots, x_d, 1]$

- $\theta_{new} = [\theta_1, \ldots, \theta_d, \theta_0]$
- New: $h(x;\theta_{new}) = sign(\theta^T_{new} x_{new})$
- $= sign(\theta^T x + \theta_0)$ (as $1 \times \theta_0 = \theta_0$)

> If data is linearly separable not through the origin, then in one dimension up the data is linearly separable, through the origin using a bias

## Polynomial Basis

- Parameter $k$ (order)

| $k$ | $d=1$         | general ($\mathbb{R}^d$)                                                               |
| --- | ------------- | -------------------------------------------------------------------------------------- |
| $0$ | $[1]$         | $[1]$                                                                                  |
| $1$ | $[1, x]$      | $[1, x_1, \ldots, x_d]$                                                                |
| $2$ | $[1, x, x^2]$ | $[1, x_1, \ldots, x_d, x_1^2, x_1 x_2, x_1 x_3, \ldots, x_2^2, \ldots, x_d^2, \ldots]$ |

## Strategies

- Discrete data
  - Numeric $\mathbb{R}$
    - May not be good for much data, 2.5, working with strings etc.
  - One-hot encoding: $m$ Booleans $[1,0,0,\ldots, 0], [0,1,0,\ldots,0],\ldots,[0,0,0,\ldots,1]$
    - Set 1 to the value you want to choose
    - 1 and only one value can be chosen
  - Factoring
    - e.g. blood types: A+, A-, B+, B-, AB, O+, O-
    - $\implies [A, B, AB, O], [+, -]$ or
      - $\implies [A, notA], [B, notB], [+, -]$
  - Text: Bag of words (bow), word2vec

## Standardising numerical features

$$\large \tilde{x}_i = \frac{x_i - \bar{x}_i}{\sigma_i}$$
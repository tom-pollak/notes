---
date created: 2022-03-11 18:08
---

# Regression

## Loss functions

### Squared loss

$Loss(guess, actual) = (guess - actual)^{2}$

#### Ordinary least squares

> Find hypothesis that minimizes the squared loss

##### OLS solution using optimization

We want $\theta^{*}, \theta^{*}_{0} = \underset{\theta, \theta_{0}}{argmin} J(\theta, \theta_{0})$

$$\LARGE \theta^{*} = (X^{T}X)^{-1} X^{T}Y$$
Where $X$ is the matrix of data ($n \times d$) and $Y$ is the column vector of labels ($n \times 1$)

- We assume there is a feature of just 1s, so we can ignore $\theta_0$

## Regularization by Ridge Regression

If the matrix $X^{T}X$ is not invertible, it means that the parameters $\theta$ is not well specified, and there is no good answer to what is the $\theta^{*}$ that minimizes the objective

In the case of the problem being underspecified, we can add a regularizer, which will keep the solution from getting too complicated

$$\LARGE \theta^{*}_{ridge} = (X^{T} X + n \lambda I)^{-1}X^{T}Y$$

- We make the matrix more diagonally dominant, to make the matrix invertable
- Penalizes the magnitude of $\theta$, so we can keep it from overfitting with the data

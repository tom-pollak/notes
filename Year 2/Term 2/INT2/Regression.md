---
date created: 2022-03-11 18:08
---

# Regression

## Loss functions

### Squared loss

$Loss(guess, actual) = (guess - actual)^{2}$

#### Ordinary least squares

> Find hypothesis that minimizes the **squared loss**

##### OLS solution using optimization

$$J(\theta, \theta_{0}) = \frac{1}{n}\sum\limits^{n}_{i=1} (\theta^{T} x^{(i)} + \theta_{0} - y^{(i)})^{2}$$
We want $\theta^{*}, \theta^{*}_{0} = \underset{\theta, \theta_{0}}{argmin}\ J(\theta, \theta_{0})$

$$\LARGE \theta^{*} = (X^{T}X)^{-1} X^{T}Y$$
Where $X$ is the matrix of data ($n \times d$) and $Y$ is the column vector of labels ($n \times 1$)

- We assume there is a feature of just 1s, so we can ignore $\theta_0$

## Regularization by Ridge Regression

If the matrix $X^{T}X$ is not invertible, it means that the parameters $\theta$ is not well specified, and there is no good answer to what is the $\theta^{*}$ that minimizes the objective

In the case of the problem being underspecified, we can add a regularizer, which will keep the solution from getting too complicated

$$\LARGE \theta^{*}_{ridge} = (X^{T} X + n \lambda I)^{-1}X^{T}Y$$

- We make the matrix more diagonally dominant, to make the matrix invertable
- Penalizes the magnitude of $\theta$, so we can keep it from overfitting with the data


### Ridge regression using [[Gradient Descent in Multiple Dimensions|gradient descent]]

- Inverting a matrix can be very computationally expensive
	- $X^{T}X$ is $d \times d$ matrix which is not hard to invert
	- However computing $X^{T}X$ is hard to compute as the dimensions are $d \times n$ and $n \times d$
		$n$ num of training examples – can be millions
		$d$ dimensions of data
	- So matrix inversion is $O(d^{3}n)$
		- $d^{3}$ from inversion
		- $n$ from $X^{T}X$ - hard
- We can apply gradient descent to the problem

$$\nabla_{\theta}J_{ridge} = \frac{2}{n} X^{T}(X\theta - Y) + 2\lambda\theta$$
- Complexity $O(d \times n)$
- Gradient descent might just find local minima?
	- Ordinary least squares (above) and ridge regression are both convex functions so will always find global minima (if we find optimal step size)

#### Stochasticradient descent
- Objective has the form of a sum, instead of summating all the elements:
	- Sample a random element of the summation
	- Do a small step in that direction
	- Average of all those elements will be a good gradient
	- Computationally cheaper
	- Don't need to sum of **all** training examples, a few will be just as good

$$\nabla_{\theta}J_{ridge} = \frac{2}{n} \left[ \sum\limits^{n}_{i=1} \left( \theta^{T}x^{(i)} - y^{(i)} \right)x^{(i)}  \right] + 2\lambda\theta$$
	
![[Stochastic-gradient-descent.png | 400]]

where $f(\theta) = \sum\limits^{n}_{i=1}f_{i}(\theta)$

So randomly compute one value from $f$ ($f_i$)


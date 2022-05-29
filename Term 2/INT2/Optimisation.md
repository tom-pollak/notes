---
date created: 2022-03-11 16:53
date updated: 2022-03-11 18:08
---

# Optimization

## Objective function

> Objective function $J(\Theta)$
> $\Theta^{*}= \underset{\Theta}{argmin} J(\Theta)$

$\LARGE J(\Theta) = \left( \frac{1}{n} \mathcal{L}(h(x^{i;}\theta), y^i) \right) + \lambda R(\Theta)$

> $\lambda R(\Theta)$: Regularization constant, where we can weigh the function

## Logistic regression

> (Linear logistic classifier)

Does the perceptron algorithm minimize 0 1 loss on the dataset

- Under what conditions?
- Promises to find a linear separator if data is linearly separable.
- If not, perceptron does not guarantee anything.

Before: $\large \mathcal{L}_{01} (g, a) = \left\{ \text{1 if g } \neq \text{ a} \atop \text{0 otherwise} \right.$

> Minimizing $0 1$ loss is [[NP#NP-Hard]], from its lack of smoothness

#### Lack of smoothness

Let two hypotheses ($H$ and $H_0$) where one can be closer in parameter space, to the perfect values, but they both make the same number of misclassifications so have the same objective value.

Both of these lines look the same to the optimizer, impossible for the optimizer to know which one to expand on

#### No degree of certainty

- All results must  be categorical,  1 or -1.
- If a point is closer to the linear separator, then we may be less certain about the outcome, however no way of expressing it.

### How to smooth out classifications with the sigmoid function

> $\large LLC(x;\theta;\theta_{0})= \sigma(\theta^{T}x + \theta_0)$

We use the sigmoid function to smooth out the classifications that we are less certain on

Sigmoid: $\large \sigma(z) = \frac{1}{1 + e^{-z}}$

This will give us a value between 0 and 1 to give a certainty for our prediction

### Making LLC into a classifier

- To make a classifier, predict +1 when $\sigma(\theta^{T}x + \theta_{0})> 0.5$
- For $\sigma(z) > 0.5$, $z > 0$

## Negative log likelihood loss function

> Loss on all data inversely related to probability that $\theta, \theta_0$ assign to my data

$\large \prod\limits_{i=1}^{n} \left\{ g^{i} \text{   if } y^{i} = 1 \atop 1 - g^{i} \text{    otherwise (if } y^{i}= 0) \right.$
Where $y^i$ is the label (0 or 1) and $g^i$ is the guess (sigmoid function)

Maximal if all our guesses are right, if a guess is wrong (0) then it will give 0

This is equivalent to:

$\LARGE \prod_{i=1}^{n} g^{(i)^{y^{(i)}}}\cdot (1 - g^{i})^{(1 - y^{(i)})}$

> Problem: the sigmoid function will never output 0 or 1, but values extremely close (0.99999), with a large training set, this can decrease the loss function

We can use the log function as it is a monotonic function, where transforms the values, but not the location. This is ideal as we are after the $argmin$ of $\theta$, not the values itself.

$\LARGE = -\sum\limits\limits_{i=1}^{n} (y^{i} log(g^{i}) + (1 - y^{i}) log(1-g^{i}))$

- Negative as we want to minimize the function
- This is the **negative log likelihood function**

$\LARGE = \sum\limits_{n}^{i=1} \mathcal{L}_{NLL}(g^{i},y^{i})$
Where

$\LARGE L_{NLL}(g,y) = -(ylog(g) + (1 - y) log(1 - g))$

$L_{NLL}$ can be called cross-entropy or log loss function

## Regularization

> $\lambda R(\Theta)$ from the [[Optimisation#Objective function]]

Within a hypothesis class, we may prefer some hypothesizes to others

Typical choices:

- $R(\Theta) = ||\Theta - \Theta_{prior}||^2$ - If we have a previously calculated $\Theta$, then we might want the new $\Theta$ to be similar
- $R(\Theta) = ||\Theta||^{2}$ - Don't make it too complicated, prefer a simple solution

## Logistic Regression objective

$\LARGE J_{LR}(\theta, \theta_{0}; \mathcal{D}) = \left( \frac{1}{n}\sum\limits^{n}_{i=1} \mathcal{L}_{NLL}(\sigma(\theta^{T} x^{(i)} + \theta_{0}), y^{(i)}) \right) + \lambda||\theta||^{2}$

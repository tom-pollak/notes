---
date created: 2022-01-18 17:07

---

# Supervised Learning

## Hypothesis

> $y = h(x; \theta)$
> Where $h \in \mathcal{H}$

## Loss function

> $L(g, a)$
> Guess and answer where, $g \in \{ +1, -1 \}$, $a \in \{ +1, -1 \}$

## Evaluating hypothesis

- Ideally: small loss on **new** data
- Small loss on training data

> $\large \mathcal{E}_n(h) = \stackrel{n}{\sum}_{i=1} L(h(x^i), y^i)$

- Training error: for each piece of training data, the algorithm will make a guess ($h$) then evaluate this with the true answer ($y$), to compute the loss function.


## Linear classifiers

> $\Large h(x; \theta, \theta_0) = sign(\theta^T x + \theta_0) = \left\{ +1 \text{ if > 0} \atop{-1 \text{ otherwise}} \right.$
> Dot product of $\theta$ and $x$ + $\theta_0$

> $x \in \mathbb{R}^d, \theta \in \mathbb{R}^d, \theta_0 \in \mathbb{R}$
> Theta is a column vector


- Line is represented by where the dot product is 0

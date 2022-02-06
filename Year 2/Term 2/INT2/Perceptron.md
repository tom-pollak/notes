---
date created: 2022-02-06 19:34

---

# Perceptron

> Find parameters that separate our data with a linear classifier

- Uses data and adjusts each piece of data

## Perceptron through origin

```
perceptron(D, T)
\theta = zeros(d); \theta_0 = 0
for t=1 to T
	for i=1 to n}
		if y^i(\theta^T x^i + \theta_0) \leq 0:
			\theta = \theta + y^i x^i
			\theta_0 = \theta_0 + y^i
return (\theta, \theta_0)
```

- If misclassify, $if$ will be less than 0
- $y$ (+1 or -1) determines what the correct will be based on whether y is positive or negative
  - $\theta = \theta + y^i x^i$ make theta more positive/negative (with the result) since it got the wrong answer
  - Same with $\theta_0$

## Linear separability

- For all data points, there exists a $\theta$ such that we can classify it without mistake

> If there is some $\theta$ such that $y^i (\theta^T x^i + \theta_0) \gt \forall i$

### Margin

#### Perpendicular distance from origin to hyperplane

![[margin.png]]

>  If the point is on the positive side of the hyperplane the distance should be positive and vice versa

Compute the distance
- Projection of vector $G$ onto vector $H$: $\frac{G \cdot H}{||H||}$
	- $G$ being random vector from the plane to the origin
	- $H$ being $\theta$ vector
>  $\large \frac{(\begin{bmatrix}0 \\ 0 \end{bmatrix} - x) \cdot \theta}{||\theta||} = \frac{-x^T \theta}{||\theta||}$

As the hyperplane equation: $\theta^T x + \theta_0 = 0$
$\implies \theta_0 = -\theta^T x$ (Matrices are commutative)

> $\large \therefore \frac{\theta_0}{||\theta||}$

#### Perpendicular distance from any point to hyperplane

- Instead of $\begin{bmatrix}0 \\ 0 \end{bmatrix}$ we have vector $P$

$\large \frac{(P - x)^T \cdot \theta}{||\theta||} = \frac{P^T \theta - x^T \theta}{|| \theta ||}$

>  $= \frac{P^T \theta - \theta_0}{||\theta||}$ - Distance from any point to hyperplane

#### Calculating margin

- Margin of a data point $(x, y)$  w.r.t. a separator $\theta_0$

> $\large y \cdot \frac{\theta^T x}{|| \theta ||}$


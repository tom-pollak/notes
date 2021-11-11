---
date created: 2021-11-10 14:21

---

# Gradient Descent

If function $f(x)$ is differentiable, we can use gradient descent
Can be used for [[Local Search]]

> $x_{n+1} = x_n - \eta \cdot f'(x_n)$
>
> - $\eta:$ step size
> - Vary step size with gradient of $f(x)$

- Effective for finding the closest min point
- Don't need to know original fitness function — only care about gradient

## Multidimensionality

Can't use $f'(x)$. We need to update our definition to use partial derivatives.

$\left\{ \stackrel{x_{n+1} = x_n - \eta \cdot \frac{\delta}{\delta x_n} f(x_n, y_n)}{y_{n+1} = y_n - \eta \cdot \frac{\delta}{\delta x_n} f(x_n, y_n)} \right.$


We get ridges in higher dimensions:
![[ridges-higher-dimensions.png]]

## Extensions

- **Shotgun GD:** Runs multiple successive GDs with different starting points and keeps track of best solution
- **Steepest-descent GD:** Look at neighbours and picks highest $f'(x)$
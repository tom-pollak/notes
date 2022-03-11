---
date created: 2022-03-11 18:08
---

# Gradient Descent

[[Year 2/Term 1/INT1/Gradient Descent | INT1 Gradient Descent]]

No way to know what the optimal step size will be

## Higher dimensions

$\large gradient\_descent(\theta_{init}, f, \nabla_{\theta}f, \eta, \epsilon)$

Where $\nabla_{\theta}$ is the gradient at point theta

$f(\theta_{1}, \ldots, \theta_{M}) \quad \theta : m \times 1$

$\nabla_{\theta} f$ is a partial function to be applied to $\theta^{i}$
$\nabla_{\theta} f: \quad m \times 1$
$\nabla_{\theta} f = \begin{bmatrix}  \frac{\delta f}{\delta_{\theta_{1}}}\\ \frac{\delta  f}{\delta_{\theta_{2}}} \\ \vdots \end{bmatrix}$

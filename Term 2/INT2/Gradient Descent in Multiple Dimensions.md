# Gradient Descent in Multiple Dimensions
[[Gradient Descent]]


$$\text{gradient\_descent}(\theta_{init}, f, \nabla_{\theta}f, \eta, \epsilon)$$
$$\theta^{(t)}= \theta^{(t-1)} - \eta \nabla_{\theta}f(\theta^{(t-1)})$$

- $\theta_{init}$:
- $f$: function of $M$ parameters $f(\theta_{1}, \ldots, \theta_{M})$, $\theta: m \times 1$
- $\nabla_{\theta} f$: Gradient of $f$ with respect to $\theta$,       $\nabla_{\theta} f: m  \times 1$
	- Vector of partial derivatives

$$\nabla_{\theta} f = \begin{bmatrix} \frac{\delta f}{\delta_{\theta_{1}}}\\ \frac{\delta f}{\delta_{\theta_{2}}} \\ \vdots \\ \frac{\delta f}{\delta_{\theta_{M}}} \end{bmatrix}$$


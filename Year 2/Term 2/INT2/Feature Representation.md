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
# Perceptron

```
\text{perceptron(D, T)}
\theta = zeros(d); \theta_0 = 0
\text{for t=1 to T}
\text{for i=1 to n}
		\text{if } y^i(\theta^T x^i + \theta_0) \leq 0:
			\theta = \theta + y^i x^i
			\theta_0 = \theta_0 + y^i
\text{return} (\theta, \theta_0)
```
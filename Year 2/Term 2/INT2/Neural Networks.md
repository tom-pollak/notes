# Neural Networks

## Neurons

![[neuron.png | 300]]


- $x$: input
- $w$: weight ($\theta$)
- $\sum$: Neuron
	- Linear unit, computes $w^{T}x + w_{0}$
- output $z$
- $f$: activation function
	- Non-linear
	- [[Optimisation#How to smooth out classifications with the sigmoid function |Linear logistic classifier]]: sigmoid function
	- [[Year 2/Term 1/DAT2/Supervised Learning#Linear]]: Identity function
	
-  Activation $a$

$$a = f(z) = f \left[ \left( \sum\limits^{d}_{j=1} x_{j}w_{j} \right) + w_{0} \right]$$

## Layers

> Collection of units

### Fully connected

$\#outputs = \#units = m$

- Activation function is the same for each unit
- Different weights

Construct a matrix of weights

$W: d \times m$, each weight has $d \times 1$
$W_{0}: m \times 1$

$$A = f(Z) = f(W^{T}X + W_{0})$$
$f: \mathbb{R} \rightarrow \mathbb{R}$

Apply elementwise: $f\left( \begin{bmatrix} z_{1} \\ \vdots \\ z_{m} \end{bmatrix} \right) = \begin{bmatrix} f(z_{1}) \\ \vdots \\ f(z_{m}) \end{bmatrix}$ 

## Multiple layers

![[layers.png]]

- Usually all activation functions in one layer are the same
- Feed forward network
	- Values can only go forward
	- Directed acyclic graph

## Activation functions

### Identity function

$f(x) = x$

$A^{L} = W^{L^{T}}A^{L-1}$
$A^{L}= W^{L^{T}}W^{(L-1)^{T}} \cdots W^{1^{T}} \times X$
$A=W^{total^T}X$

- So multiple identity activation layers are useless as we can just represent them as a single matrix

Use of neural network is for non-linear hypothesis which require non-linear activation functions

### Step function

> Function that changes from 0 to 1 sharply at 0

- Not useful as not differentiable, so gradient descent does not work

### Sigmoid function

- Takes $Z$ transforms it to a number between 0 and 1

$$\sigma(z) = \frac{1}{1+e^{-z}}$$

### ReLU

> Rectified linear unit

![[relu-function.png]]

- Non-linear
- Non-differentiable
- If input is small value, output is 0
	- Network can learn to turn some units off by giving value $\leq 0$

## Training

[[Year 2/Term 2/INT2/Supervised Learning]]

- Define loss function
- Gradient descent

## Error back-propagation
- Computes gradient
- Chain rule

Let last output be $y$

$C_{0} = (a^{(L)} - y)^{2}$
$z^{(L)} = w^{(L)}a^{(L-1)}+b^{(L)}$
$a^{(L)} = \sigma(z^{(L)})$

![[backpropagation.png | 500]]

- $a^{(L-1)}$ has its own branch with its own weight and bias

How sensitive is cost ($C$) to weight ($W^{(L)}$)?

- $\large \frac{\delta C_{0}}{\delta w^{(L)}}$
- $\delta w^{(L)}$ causes some nudge to $\delta z^{(L)}$ which causes some nudge to $\delta a^{(L)}$ which causes some nudge to $\delta C_{0}$

### Chain rule

$$\frac{\delta C_{0}}{\delta w^{(L)}} = \frac{\delta z^{(L)}}{\delta w^{(L)}} \frac{\delta a^{(L)}}{\delta z^{(L)}} \frac{\delta C_{0}}{\delta a^{(L)}}$$

- Notice derivates diagonally chained to cancel out

For a single input chain in a neural network:

$C_{0} = (a^{(L)} - y)^{2}$

- Obviously real neural networks have more than one input
- We can use subscript to represent which neuron of the previous layer it is

![[multiple-neural-inputs.png]]

$$C_{0} = \sum\limits^{n_{L} - 1}_{j=0} (a_{j}^{(L)} - y_{j})^{2}$$

- Let us call the weight connecting the $k_{th}$ neuron to the $j_{th}$ neuron $w_jk$


$\frac{\delta C_{0}}{\delta a^{(L)}} = 2(a^{(L)} - y)$

$\frac{\delta a^{(L)}}{\delta z^{(L)}} = \sigma'(z^{(L)})$

$\frac{\delta z^{(L)}}{\delta w^{(L)}} = a^{(L-1)}$

- This is for a **specific training example**

To get true gradient, we need the average of **all** training examples
$$\frac{\delta C}{\delta w^{(L)}} = \frac{1}{n} \sum\limits^{n-1}_{k=0} \frac{\delta C_{k}}{\delta w^{(L)}}$$

And that is only one component of the gradient vector

$$\large \nabla C = \begin{bmatrix} \frac{\delta C}{\delta w^{(1)}} \\ \frac{\delta C}{\delta w_0^{(1)}} \\ \vdots \\ \frac{\delta C}{\delta w^{(L)}} \\ \frac{\delta C}{\delta w_0^{(L)}} \end{bmatrix}$$
- $w_0$ is the bias (may also be represented as $b$)
- Sensitivity to bias just switches out $w$ for $w_0$
	- $\frac{\delta z^{(L)}}{\delta b^{(L)}} = 1$

Of course then we can get [[Regression#Stochasticradient descent]]
---
date created: 2021-12-08 10:05

---

# Space Complexity

- Only consider decidable [[Turing Machine]]

> $s_m: \mathbb{N} \rightarrow \mathbb{N}$ where $s_M(n)$ is a maximum number of tape squares $M$ can visit on any input length $n$
>
> - Can be on reject state

> $s_M(n) \leq \tau_M(n) + 1$
>
> - Where $\tau_M(n)$ is [[Time Complexity]]

## Growth rate of functions

Given functions $f, g: \mathbb{N} \rightarrow \mathbb{R}^+$, $f$ is of **order** $g$ if there are positive integers $c$ and $n_0$ such that:

> Order: $f(n) \leq c \cdot g(n)$ for all $n \geq n_0$

The class of all functions of order $g$ is denoted by $O(g)$, so $f \in O(g)$

e.g.

- For $f: n \mapsto n^2 +2n +5$ and $g: n \mapsto n^2$, $f \in O(g)$
- For $f': n \mapsto n^3$ and $g: n \mapsto n^2$, $g \in O(f')$ but $f' \notin O(g)$

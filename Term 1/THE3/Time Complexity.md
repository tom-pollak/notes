---
date created: 2021-11-18 10:52

---

# Time Complexity

- Only consider decidable [[Turing Machine]]

> Turing machine $M$ is the function $\tau_m: \mathbb{N} \rightarrow \mathbb{N}$, where $\tau_m(n)$ is maximium number of transitions $M$ can make on any input of length $n$
>
> - Can be to a reject state

For every k-tape TM $M$ there is a TM $M'$ such that:

- $L(M') = L(M)$ and $\tau_{M'} \in O(\tau_M^2)$
- Convert a multi tape machine to single tape with only a $O(n^2)$ increase

Let $f: \mathbb{N} \mapsto \mathbb{N}$ be a _total computable function._ Then there is a decidable language $L$ such that for every TM $M$ accepting $L$, $\tau_M$ is not bounded by $f$

- There are arbitrarily complex languages

There is a decidable language $L$ such that for every TM $M$ accepting $L$, there is a TM $M'$ such that $L(M') = L(M)$ and $\tau_{M'} \in O(log_2(\tau_M))$

- Always an infinite number of exponentially faster TM!
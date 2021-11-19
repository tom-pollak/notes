---
date created: 2021-11-19 15:46

---

# Inclusions Between Complexity Classes

> A language is **tractable** if $L \in P$
> A [[Decision Problems]] $P$ is tractable if $Y(P) \in P$

> Language **decidable in exponential time** ($ExpTime$) if [[Turing Machine]] deciding $L$ such that $\tau_M \in O(2^{n^r})$ for some $r \in \mathbb{N}$

- $P \subseteq NP \subseteq PSpace = NPSpace \subseteq ExpTime$
- $P \neq ExpTime$

> #### Proofs on slides lecture 18


## Presburger Arithmetic

> Theory of natural numbers using constants 0 & 1, + & =

The problem to decide whether a given formula follows the axioms requires time $\Omega(2^{2^{cn}})$, a lower bound and hence **not in $ExpTime$**

---

[[Time Complexity]] [[Space Complexity]]
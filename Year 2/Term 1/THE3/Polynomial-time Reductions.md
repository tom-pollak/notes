---
date created: 2021-12-08 10:05

---

# Polynomial-time Reductions

> For function $f$ if there is a [[Turing Machine]] M with $\tau_M \in O(n^r)$ that computes $f$

Let $L_1, L_2 \subseteq \Sigma^*$ be languages. $L_1$ is **polynomial-time reducible** to $L_2$ if there is a poly-time computable total function $f: \Sigma^* \rightarrow \Sigma^*$ such that for all $x \in \Sigma^*$

> $x \in L_1 \iff f(x) \in L_2$

Given decision problems $P_1, P_2$ we say $P_1$ is poly-time reducible to $P_2$ if $Y(P_1)$ is poly-time reducible to $Y(P_2)$

If $L_1$ is poly-time reducible to $L_2$, then $L_1$ is “no harder” than $L_2$. Equivalently, $L_2$ is “at least as hard” as $L_1$. (Considered equally hard if their time complexities differ at most by a polynomial)

> #### Huge proof on lecture 19

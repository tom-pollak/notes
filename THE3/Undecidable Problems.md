---
date created: 2021-11-04 13:27

---

# Undecidable Problems

> [[Decision Problems#Membership Problem]] for [[Semidecidable Languages]] is undecidable but semidecidable

## Reducing [[Decision Problems]]

> Solvability of B implies solvability of A

- Construct a solver for A that may use a solver for B
- Usually A is simpler than B

Let $L_1, L_2 \subseteq \Sigma^*$. $L_1$ is reducable to $L_2$ if there is a computable total function $f: \Sigma^* \rightarrow \Sigma^*$ such that for all $x \in \Sigma^*$

> $x \in L_1$ iff $f(x) \in L_2$

Given decision problems $P_1, P_2$ we say that $P_1$ is reducible to $P_2$ if $Y(P_1)$ is reducible to $Y(P_2)$

### Reducing Self-accepting problem to membership problem

$Y(SAP) = \lbrace e(M)\ |\ M\ is\ a\ TM\ and\ e(M) \in L(M) \rbrace$
$Y(MP) \ = \lbrace e(M)e(w)\ |\ M\ is\ a\ TM\ and\ w \in L(M) \rbrace$

N.B $e(M)$ is an encoded M

Define $f: \lbrace 0,1 \rbrace^* \rightarrow \lbrace 0, 1 \rbrace^*$ by

$f(x) = \lbrace xe(x)\ if\ x = e(M)\ for\ some\ TM\ M,$
$\ \ \ \ \ \ \ \ \ \ \ \ \ \lbrace \Lambda\ \ \ \ \ \ otherwise$

Then $f$ is computable and satisfies for all $x \in \lbrace 0, 1 \rbrace^*$

> $x \in Y(SAP)$ iff $f(x) \in Y(MP)$

Hence reduces SAP to MP

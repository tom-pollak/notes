---
date created: 2021-12-04 14:20
date updated: 2021-12-04 14:21

---

# NP

> Set of all [[Decision Problems]] that can be **verified** in polynomial time ($O(n^k)$) by a deterministic [[Turing Machine]]

## P

> Set of all decision problems that can be **solved** in polynomial time by a deterministic Turing machine

- Most people assume $NP \neq P$ and $NP \subset P$ however this has not been proved

## NP-Complete

> A problem $x$ that is in [[NP#NP | NP]] is also NP-Complete iff every other problem in $NP$ can be transformed into $x$ in polynomial time

1. $x$ is in $NP$
2. Every problem in $NP$ is reducible to $x$

- If any NP-Complete problem was to be solved quickly, then all NP problems can be solved quickly

### Satisfiability problem

Consider an expression in [[SAT Solving#Conjunctive Normal Form]] with boolean expressions built from literal variables.

- An expression $C$ is **satisfiable** if there is an assignment of truth values to variables, making $C$ true

> Question: For the boolean expression $C$ in conjunctive normal form, is $C$ satisfiable?

#### 3-Sat

- Variation where each disjunction contains at most 3 literals

> ##### Complete Subgraph Problem (clique problem)
>
> For a graph $G$ and $k \geq 1$
> Does $G$ have a complete subgraph with $k$ vertices?

#### Reducing Sat to Clique Problem

- We need to construct a polynomial-time computable function $f$ which maps a CNF expression to a pair $(G_x, k_x)$, where $G_x$ is a graph and $k_x$ an integer, such that $x$ is satisfiable iff $G_x$ contains a clique with $k_x$ nodes


## NP-Hard

> Problems that are at least as hard as the hardest problems in [[NP#NP | NP]]

- [[NP#NP-Complete | NP-Complete]] are also NP-Hard
- Not all NP-Hard problems are NP or a decision problem!
  - NP in NP-Hard does not mean non-deterministic polynomial time

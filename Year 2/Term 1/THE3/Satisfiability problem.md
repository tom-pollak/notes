---
date created: 2021-12-08 16:06
date updated: 2021-12-08 16:17

---

# Satisfiability problem

> First problem to be [[NP#NP-Complete]]

Consider an expression in [[SAT Solving#Conjunctive Normal Form]] with boolean expressions built from literal variables.

- An expression $C$ is **satisfiable** if there is an assignment of truth values to variables, making $C$ true

> Question: For the boolean expression $C$ in conjunctive normal form, is $C$ satisfiable?

## 3-Sat

- Variation where each disjunction contains at most 3 literals

> ##### Complete Subgraph Problem (clique problem)
>
> For a graph $G$ and $k \geq 1$
> Does $G$ have a complete subgraph with $k$ vertices?

## Reducing Sat to Clique Problem

- We need to construct a polynomial-time computable function $f$ which maps a CNF expression to a pair $(G_x, k_x)$, where $G_x$ is a graph and $k_x$ an integer, such that $x$ is satisfiable iff $G_x$ contains a clique with $k_x$ nodes

> Suppose we pick one literal $L_i$ from each conjunct (AND) as a node, and connect each pair of picked literals that are not complementary by an edge. If this yields a complete graph, then $x$ is satisfiable by the assignment: $x_i \mapsto$ _if_ $x_i \in \lbrace L_1, \cdots , L_2 \rbrace$ _then_ true _else false_
>
> - Vice versa, if $x$ is satisfiable, then a complete graph can be constructed this way

- We construct $G_x$ as a graph consisting of all occurrences of literals in $x$, and all edges between literals that are in **distinct** conjuncts and not complementary (e.g. $x$ and $\neg x$. Also, we choose $k_x$ as the number of conjuncts in $x$. Then $G_x$ contains a clique with $k_x$ nodes iff $x$ is satisfiable.

![[sat-to-clique.png]]

> ##### Definition
>
> $x = \bigwedge \limits_{i=1}^{c} \bigvee \limits_{j=1}^{d_i} a_{i, j}$
> Where each $a_i, j$ is a literal. Define $G_x = (V, E)$ by
> $V = \lbrace (i, j)\ |\ 1 \leq i \leq c \text{ and } 1 \leq j \leq d_i \rbrace$
> $E = \lbrace \lbrace (i, j), (l, m) \rbrace\ |\ i \neq l \text{ and } a_{i,j} \not\equiv \neg a_{l,m}$

> We show that $f: x \mapsto (G_x, k_x)$ reduces Sat to clique problem
>
> #### Proof lecture 21

## Satisfiability is NP-Complete

> Show that Sat is in [[NP#NP]] and that it is in [[NP#NP-Hard]]

### Sat is in NP

Describe [[Nondeterministic Turing Machine]] $N$ which accepts Sat's language of encoded yes-instances in polynomial time. $N$ first checks whether input is a boolean expression $C$ in [[SAT Solving#Conjunctive Normal Form]], which can be done in deterministic polynomial time. If input is not a CNF, $N$ stops without accepting.

Next, $N$ uses a guess-and-check strategy to determine if $C$ is satisfiable. It guesses an assignment of truth variables and checks whether this assignment makes $C$ true. If so, $N$ accepts.

- Guessing implemented by instantiating each occurrence of a variable $x$ with 1 or 0 for all variables in $C$.
- Choice made using $N$'s non-deterministic transition.
- When all variables have been instantiated, $N$ checks whether the resulting expression evaluates to true or false. This can be done in deterministic polynomial time.

> ##### How does it satisfy in **deterministic** polynomial time if there are $2^n$ combinations of boolean values, where $n$ is the number of boolean literals?
>
> - Seems to use a nondeterministic Turing machine to instantiate the combinations but even so the deterministic Turing machine must evaluate every combination?

### Sat is NP-Hard

Consider any language $L$ in $NP$. All we know there exists NTMs that accept $L$ in polynomial time. Let $N$ be one of those machines.

- The idea of reduction is to translate a string $w$ into a CNF expression $C$ that simulates $N$ on input $w$.
  - For each accepting computation of $N$ on input $w$, $C$ has a satisfying assignment corresponding to that computation.
  - If no computation of $N$ on input $w$ accepts, $C$ is unsatisfiable
    - Hence $w$ in $L$ iff $C$ is satisfiable.

#### Create a tableau of configurations

Construction of $C$: Introduce a _tableau_ consisting of configurations of a computation $N$ on $w$.

Let $k$ be a constant such that $N$ runs in time $n^k$ for inputs of length $n$

- Actually assume $N$ runs in time $n^k - 4$ - for technical reasons

A tableau for $N$ on $w$ ($n^k \times n^k$)

| $\#$ | $q_0$ | $\Delta$ | $w_1$ | $w_2$ | $\cdots$ | $w_n$ | $\Delta$ | $\cdots$ | $\#$ |
| ---- | ----- | -------- | ----- | ----- | -------- | ----- | -------- | -------- | ---- |
| $\#$ |       |          |       |       |          |       |          |          | $\#$ |
| $\#$ |       |          |       |       |          |       |          |          | $\#$ |

- For convenience, we assume each configuration starts and ends with $\#$
- The first row is start configuration of $N$ on $w$ with each row following according to a transition of $N$
  - If no transitions left, then subsequent rows filled with final configuration
- A tableau is _accepting_ if contains an accepting configuration

> $N$ accepts $w$ iff there exists an accepting tableau for $N$ on $w$

#### Translation of $w$ into CNF $C$

Let $S = Q \cup \Gamma \cup \{\#\}$ where $Q$ and $Gamma$ are state set and tape alphabet of $N$

For all $1 \leq i,j \leq n^k$ and $s \in S$ let $x_{i,j,s}$ be a boolean variable

> $x_{i,j,s}$ has value 1 iff $cell[i,j]$ contains $s$
>
> - Where $cell[i,j]$ is cell in tableau

Design $C$ such that a satisfying assignment to its variables corresponds to an accepting tableau for $N$ on $w$

> Let $C = C_{cell} \wedge C_{start} \wedge C_{move} \wedge C_{accept}$

- $C_{cell}$: Turns on exactly one variable for each cell
  - Any satisfying assignment for $C$ must have exactly one variable turned on for each cell of the tableau
    - Specifies unique symbol for that cell
- $C_{start}$: First row of a tableau is the initial configuration of $N$ on $w$
- $C_{accept}$: Guarantees that the tableau is accepting, by requiring the occurrence of the accept state
- $C_{move}$: Each pair of adjacent rows is related by a move according to $N$'s transition function.
  - Achieved by specifying that each $2 \times 3$ window of cells is _legal_
  - All windows in table are legal

##### Legal windows

| a     | $q_1$ | b |
| ----- | ----- | - |
| $q_2$ | a     | c |

| a | $q_1$ | b     |
| - | ----- | ----- |
| a | a     | $q_2$ |

| b   | b   | b   |
| --- | --- | --- |
| c   | b   | b   |

##### Illegal windows

| a | b | a |
| - | - | - |
| a | a | a |

| a     | $q_1$ | b |
| ----- | ----- | - |
| $q_2$ | a     | a |

- Last one is illegal as transition does not exist

> #### Proof that the rules work: Lecture 22 pg 11

#### Proof $C$ can be constructed from $w$ in polynomial time

Estimate number of variables in $C$: Tableau is $n^k \times n^k$, hence contains $n^{2k}$ cells
- Each cell has $I$ variables associated with it, where $I$ is num symbols in $S$
	- $I$ depends only on $N$ not on input length $n$, total number of variables is in $O(n^{2k})$

Estimate size of each of four parts of $C$:
- $C_{cell},\ C_{move}\ \&\ C_{accept}$: Contain fixed size fragment of the expression for each cell of tableau, so $O(n^{2k})$
- $C_{start}$: Fragment for each cell in top row, so $O(n^k)$

$\therefore$ $C$ total size is in $O(n^{2k})$

- Estimates are low by a factor of $O(\log{n})$ as each variable has indices ranging up to $n^k$ so may require $O(\log{n})$ symbols to write the expression, but does not change polynomially of result.

We can generate $C$ in polynomial because of its repetitive nature. Each component of $C$ consists of many nearly identical fragments, which differ only at indices in a simple way. Hence, $C$ can be produced from $w$ in polynomial time.

#### $C$ is in [[SAT Solving#Conjunctive Normal Form | CNF]]

- $C_{cell}$: Written as a conjunction of disjunctions, hence in CNF
- $C_{start}$: Conjunction of variables, each of which can be taken as a disjunction of size 1
- $C_{accept}$: Disjunction of variables
- $C_{move}$: Can be converted into CNF expression such that $C_{move}$ is only increased by a constant factor (**Sipser**)
# Exam
_Y3891128_

## 1.

## 2. 

### (i)

**State representation:** The start and end points of the bridge are represented as $B_0$ and $B_1$ respectively, where each point $B_p$ is a set of integers representing each person $P_i$ at that point. We also define a variable $T$ that tracks the movement of the torch between points. The overall state is a 2-tuple of sets and a variable:

> $\langle B_0, B_1 \rangle \ \ T$

**Initial state:** Every person starts at point $B_0$, and variable $T$ is initialized as 0

> $\langle B_0: \lbrace P_1, P_2, \ldots , P_n \rbrace ,\ B_1: \lbrace \rbrace \rangle \ \ T = 0$

**Goal test:** Every person is at point $B_1$, or equivalently point $B_0$ is empty

> $\forall i \in \lbrace \mathbb{Z}^+ < n \rbrace ,\ P_i \in B_1$ or $B_0 = \emptyset$

**Successor function:** Can be defined as a series of actions with appreopiate preconditions and postconditions. Actions in this case consist of moving a set of people, $W$, defined by the function $f_W: \mathbb{N} \rightarrow \lbrace \mathbb{N},\ \lbrace \mathbb{N} \cup \lambda \rbrace \rbrace$ between the two points. For example $MOVE(W)$ would move the set of people $W$ to the point described by $T$.

Preconditions: We can define $F_W$ from $T$

> $\LARGE f_W = \left\{\ \{ P_i,\ P_j\ |\ \exists P_i,\ P_j:\ P_i \in B_0,\ P_j \in \{B_0\ \cup\ \lambda \},\ P_i \neq P_j \}\ \text{ if } T \text{ is even} \atop \{ P_i,\ P_j\ |\ \exists P_i,\ P_j:\ P_i \in B_1,\ P_j \in \{B_1\ \cup\ \lambda \},\ P_i \neq P_j \}\ \text{ if } T \text{ is odd} \right.$

We can also define the input and output points from $T$

> $\LARGE \left\{\ B_{out} = B_0,\ B_{in} = B_1 \text{ if } T \text{ is even} \atop B_{out} = B_1,\ B_{in} = B_0 \text{ if } T \text{ is odd} \right.$

Postcondtions: These reflect an updated set of states after the $MOVE$ function has taken place

> $B_{out}' = B_{out} - W$
> $B_{in}' = B_{in} \cup W$
> $T' = T + 1$

### (ii)


---
date created: 2022-01-10 15:18

---

# Exam

_Y3891128_

## 1.

### (i)

**(a)** A B C D E F G H I J K

**(b)** A B E I F C D G J K H

**(c)** A B E F C D G H I J K

**(d)** (Where "|" marks a new iteration)

A | A B C D | A B E F C D H | A B E I F C D G J K H

### (ii)

I would use a stack to represent the fringe, which is FIFO

| Add/ remove nodes from top |
| :------------------------- |
| J                          |
| H                          |
| **Bottom of the stack**    |

## 2.

### (i)

**State representation:** The start and end points of the bridge are represented as $B_0$ and $B_1$ respectively, where each point $B_p$ is a set of integers representing each person $P_i$ at that point. We also define a variable $T$ that tracks the movement of the torch between points. The overall state is a 2-tuple of sets and a variable:

> $\langle B_0, B_1 \rangle \ \ T$

**Initial state:** Every person starts at point $B_0$, and variable $T$ is initialized as 0

> $\langle B_0: \lbrace P_1, P_2, \ldots , P_n \rbrace ,\ B_1: \lbrace \rbrace \rangle \ \ T = 0$

**Goal test:** Every person is at point $B_1$, or equivalently point $B_0$ is empty

> $\forall i \in \lbrace \mathbb{Z}^+ < n \rbrace ,\ P_i \in B_1$ or $B_0 = \emptyset$

**Successor function:** Can be defined as a series of actions with appreopiate preconditions and postconditions. Actions in this case consist of moving a set of people, $W$, defined by the function $f_W: \mathbb{N} \rightarrow \lbrace \mathbb{N},\ \lbrace \mathbb{N} \cup \lambda \rbrace \rbrace$ between the two points. For example $MOVE(W, B_0, B_1, T)$ would move the set of people $W$ from point $B_{in}$ to $B_{out}$. $T$ is used to verify the other variables. The preconditions are as follows:

> $f_W(B_0, B_1, T) = \LARGE \left\{\ \{ P_i,\ P_j\ |\ \exists\ i,j:\ P_i \in B_0,\ P_j \in \{B_0\ \cup\ \lambda \},\ P_i \neq P_j \}\ \text{ if } T \text{ is even} \atop \{ P_i,\ P_j\ |\ \exists\ i,j:\ P_i \in B_1,\ P_j \in \{B_1\ \cup\ \lambda \},\ P_i \neq P_j \}\ \text{ if } T \text{ is odd} \right.$

We can also use the function to create variable _pointers_ $B_{in}$ and $B_{out}$

> $f_B(T) = \LARGE \left\{\ B_{out} = B_0,\ B_{in} = B_1 \text{ if } T \text{ is even} \atop B_{out} = B_1,\ B_{in} = B_0 \text{ if } T \text{ is odd} \right.$

Postcondtions: These reflect an updated set of states after the $MOVE$ function has taken place

> $B_{out}' = B_{out} - W$
> $B_{in}' = B_{in} \cup W$
> $T' = T + 1$

### (ii)

As with an unoptimized approach all people crossing are equivalent, a depth first search that avoids cycles would be the best because it would search deeper in the tree than a breadth first search and therefore find a solution quicker.

### (iii)

An admissible heuristic could be the person with the smallest $i$ currently at point $B_0$, divided by 2

> 

### (iv)

For an admissible heuristic, we are required to underestimate the lowest possible solving time of the problem. Therefore we can ignore the problem of the torch coming back, as this will only increase the lowest possible solving time.

As by definition of the question, the persons crossing time is $2^i$, it follows that the person with the lowest $i$ is the person with the shortest crossing time.

For the quickest _theoretical_ possible solving time every person currently at $B_0$ would have the same lowest crossing time so no other person would have to wait for somebody else (even though this is not technically possible in the current puzzle, as each person has a different time according to their identifier $i$). Therefore, as two people can cross the bridge at any one time, the lowest possible solving time by this definition must be the time of the quickest person currently at $B_0$ (lowest $i$) divided by 2.

## 3.

### (i)

- $x_0$: 0.1
- $x_1$: 0.0996
- $x_2$: 0.0992
- $x_3$: 0.0988

### (ii)

The functions minima is $x = 0$, at this point the gradient is 0 so there will be no difference between the new x value and old one so the algorithm will know it has reached the local minima. The algorithm will therefore return the minimum value on the first loop.

### (iii)

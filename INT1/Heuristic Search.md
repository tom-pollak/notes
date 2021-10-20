---
date created: 2021-10-20 16:03
date updated: 2021-10-20 16:35

---

# Heuristic Search

## Trees

> ##### Only optimal with an **admissible** heuristic

- Uninformed search works based on structure of tree and cumulative path cost
- Informed search looks at states within the node to make a more informed choice

## Graphs

> ##### Only optimal with is **consistent** heuristic

### Consistency
> Most admissible heuristics are consistent

A heuristic $h(n)$ is consistent if:

For all $n$, every successor of $n'$ of $n$ by action $a$:
- $h(n) \leq c(n, a, n') + h(n')$ 
- No way of cheating the heuristic: No shorter path than going directly to the solution

```mermaid
graph LR
n((n)) --> |c: n,a,n'| m((n')) --> |h: n'| g((G))
n --> |h: n| g
```

## Informed search

- Predict goal state can expand nodes more likely to reach goal sooner
- Evaluation function $f(n)$ is used to provide this signal allowing extra information to be used
- Common approach to defining $f(n)$ is to use a heuristic function $h(n)$
  - Typically fast to compute and provide domain specific information to search algorithm
  - e.g. Good heuristic in computing journey time is straight line distance to destination

## Heuristic Functions

> **Admissible:** Never overestimates the cost to reach the goal
>
> - e.g., straight line distance — it is **optimistic**
> - Proven through certain search functions will always find **optimal**

### Picking a Heuristic

### Uniform-cost search (UCS)

Like breadth first but nodes stored in priority queue ordered by increasing path cost

### Greedy Best-First Search

> Expand node with lowest $f(n) = h(n)$

- Always uses lowest heuristic
- Maintain priority queue by increasing $f(n)$

#### Performance

- Completeness: No
- Time Complexity: $O(b^m)$
  - (Varies according to $h(n)$)
- Space Complexity $O(b^m)$
- Optimality: No
- (This is a worst-case, a good $h(n)$ can reduce this)

### [[A-star Search | A\* Search]]

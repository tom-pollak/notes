---
date created: 2021-10-20 16:34

---

# A* Search

> $f(n) = g(n) + h(n)$
>
> - Combines $h(n)$ with current path cost $g(n)$

**Performance:**

- Completeness: Yes
  - Assuming finite tree, and step costs $\geq \epsilon$
- Time: $O(b^d)$
- Space: $O(b^d)$
- Optimality: Yes
  - Provided $h(n)$ is admissible

> Problem with GBFS and A* is that they are variants of BFS, inheriting their high space complexity

## Variations

### Iterative-Deepening

> IDA* will expand the node with the lowest $f(n)$, up to threshold $\tau$
>
> - Once fringe is empty, threshold increased to minimum cost of all $f(n)$ that exceeded $\tau$, and the search restarts

- Fringe implemented as a stack, but only pushing new node $n$ if $f(n) \leq \tau$

#### Performance

- Completeness: Yes
  - Assuming finite tree, and step costs $\geq \epsilon$
- Time: $O(b^d)$
- Space: $O(d)$
  - Linear space!
- Optimality: Yes
  - assuming admissible $h(n)$

### Simplified Memory-Bounded A*

- When bounded memory is full, prune away subtrees that have high f-values, storing the lowest f-value in the parent node of subtree
- If f-values in current subtree start to deteriorate, pruned subtree can be re-initialised and searched

#### Performance

- Completeness: Yes
  - If $d < M$ for memory bound $M$
- Time Complexity: $O(b^d)$
- Space: $O(M)$
- Optimality: Yes
  - If optimal solution is reachable, otherwise will return the best reachable solution

<br>
- Switching subtrees can cause overhead in some problems that continually switch between subtrees, increasing time

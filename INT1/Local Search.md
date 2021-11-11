---
date created: 2021-11-10 14:11

---

# Local Search

- For some problems, it is quick to produce bad solutions
- Don't care how you get there
  - e.g, finding minimum of a function wiht many parameters
- **Anytime algorithm**: always have a solution
- We don't usually have the **best** solution

> Made up of a trace of execution
> $(s_0, f_0), (s_1, f_1), ..., (s_n, f_n)$
>
> - $s_k$: members of the search space
> - $f_k$: fitness, corresponding to $s_k$

## Candidate Solution

Formal Representation:

- ~~State~~ Candidate solution
- ~~Initial state~~ start point
- ~~successor function~~ neighbourhood function
- ~~goal test~~
- ~~path cost~~
- Fitness / objective function

## Neighbours

> $\forall k, N(s_k+1, s_k)$
>
> - $N(s_a, s_b)$ is neighbourhood function for the search space

## Optimization Problems

- Given some mathematical function, how do we find the minimum?

> $arg\ \underset{x}{min}\ f(x)$

## Fitness Function

- We can sometimes just use the function we are optimizing
- Provides feedback to our algorithm of how “good” the solution is
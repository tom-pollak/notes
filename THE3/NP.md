---
date created: 2021-12-04 14:20

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

## NP-Hard

> Problems that are at least as hard as the hardest problems in [[NP#NP | NP]]

- [[NP#NP-Complete | NP-Complete]] are also NP-Hard
- Not all NP-Hard problems are NP or a decision problem!
  - NP in NP-Hard does not mean non-deterministic polynomial time

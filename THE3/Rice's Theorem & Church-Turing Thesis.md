---
date created: 2021-11-04 13:27

---

# Rice's Theorem

## Language property

> **language property**: A property $P$ of TMs if for every TM having property $P$ and every TM $M'$ with $L(M) = L(M')$, $M'$ has property $P$

- e.g. $L(M) = \emptyset$, $L(M) = \Sigma^*$ $L(M)$ is finite are language properties
- M halts on every input is not a language property
  - Two TMs that accept no input — one moves immediately to accept state and one loops infinitely on every input

> Every non-trivial language property of TMs is undecidable

# Church-Turing Thesis

 > Every effective procedure can be carried out by a [[Turing Machine]]

- Algorithm
- Partial function
- Decision problem
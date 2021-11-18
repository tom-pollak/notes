---
date created: 2021-11-18 11:23
date updated: 2021-11-18 11:30

---

# SAT Solving

> A sentence is satisfiable with some model

- First problem to be [[Propositional Logic#NP Complete]]

## Conjunctive Normal Form

- Only negations, conjunctions and disjunctions
- All negations bound to variables, not brackets
- e.g. $(\neg a \vee b) \wedge (b \vee \neg c)$

> Clauses are **constraints** on the model

### Breaking a clause

> All literals in that clause must be false

e.g. breaking both clauses:

- $(\neg a \vee b) \wedge (b \vee \neg c)$
- a: true
- b: false
- c: true

Aim to find some values that prevent any broken clauses

## SAT as Search

> Essentially a discrete optimisation problem

- Intrinsically involves searching for a solution, either in search tree (BDLL) or discrete search space
- Many AI problems can be restated as SAT problem

## DPLL

- Original SAT solver
- Essentially DFS with a few tweaks to improve performance

Improvements:
- Early termination
	- If particular clause is already satisfied/ broken
- Pure/ impure symbols
	- Literal that is invariant between clauses
	- e.g. $(A \vee \neg B) \wedge (\neg B \vee \neg C) \wedge (A \vee C)$
		- A is always true, B is always false, C is **impure**
		- However, once $B = false$, the only remaining clause with C is $(A \vee C)$ meaning C **becomes** pure
- Unit clauses: A unit clause that contains a single literal
	- If $B = true$, $(\neg B \vee \neg C)$ simplifies to $\neg C$, meaning C must be set to false
	- If all literals bar one are false in partially-built model, then fix the last one to satisfy the clause

## WalkSAT

- More efficient by relaxing need for completeness
- Useful for SAT problems we suspect are satisfiable

### Definition

- Assign random true/false values to all variables
- Loop for _max_steps_:
	- Pick a broken clause
	- With probability $p$, randomly flip one variable in that clause
	- With probability $(1 - p)$, flip whichever variable improves the objective function (reduces number of broken clauses)
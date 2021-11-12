---
date created: 2021-11-12 10:57
date updated: 2021-11-12 11:18

---

# Propositional Logic

## Knowledge-Based Agent

```
function KB-agent(percept) returns an action
	persistent: KB, a knowledge base
				t, a counter, initially 0, indicating time
	
	Tell(KB, Make-Percept-Sentence(percept, t))
	action <- Ask(KB, Make-Action-Query(t))
	Tell(KB, Make-Action-Sequence(action, t))
	t <- t + 1
	return action
```

**Tell:** Function to insert a new prop logic sentence into knowledge base

- `Tell(Rain, true)`
- `Tell(implies(Rain, Wet))`

**Ask:** Query knowledge base

- `Ask(Wet)`

**Recall:** Percept sequence

- Complete history of everything the agent has ever perceived

## Entailment

$p \models q$ says p “entails” q

- If p is true, there is no way for q to be false

Test $KB \models \alpha$?

Systematically setting each proposition symbol to be true to enumerate possibilities

If that doesn't work, need inference algorithm

### NP Complete

- Every known inference algorithm has exponential time complexity
  - Searching using inference rules as operators until we match some goal state
  - In effect deploying depth-first search

## Properties

**Equivalence:** If two sentences entail one another

**Validity:** If it is true in every model
- Tautology true in **every possible model**

**Satisfiability:** Sentence is true in at least one model
- For a reasonably sized model, it is a non-trivial problem to find allocation of values to pop symbols such that the model is true
- Known as [[SAT Solving]]
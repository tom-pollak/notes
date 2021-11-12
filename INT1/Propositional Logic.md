---
date created: 2021-11-12 10:57

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
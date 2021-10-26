---
date created: 2021-10-26 12:57

---

# Minimax

> Combines both [[Adversarial Search#MinMax Strategy | MinMax Strategy]] and [[Adversarial Search#MaxMin Strategy | MaxMin Strategy]]

- In a zero-sum game, this can consist of two players: Max and Min

## Algorithm

- Expands the game tree until it reaches the terminal node
- It then updates the minimax value of each non-terminal node as it recurses back up the tree to the root

```
FUNCTION MinimaxDecision {
	For each a in Actions do {
		VALUE[a] = MinimaxValue(Apply(a, InitialState))
	}
	return a with maximum Value[a]
}

FUNCTION MinimaxValue(state) {
	If TerminalTest(state) then return Utility(state)
	
	If Max is to move in state then
		return the highest MinimaxValue of Successors(state)
	
	return the lowest MinimaxValue of Successors(state)
}
```

## Analysis

- Time Complexity: $O(b^d)$
  - $b$ maximum no of legal moves at each point and $d$ is depth

## Evaluation Functions

- Cut off search at a given game depth
- We need payoff functions that are not final
- Quality of solution strongly dependent on quality of evaluation function

### Good properties

- Agrees with payoff function
- Not too complex to compute
- Accurately reflect chance of winning

### Weighted Linear Functions

> $E(s) = w_1f_1(s) + ... + w_nf_n(s)$
>
> - $w_i$ are weights
> - $f_i(s)$ are some features of particular game state $s$
>   - e.g. Material value function: each $w_i$ is value of piece $i$ and $f_i(s)$ is number of pieces $i$ available in state $s$

## Alpha-Beta Pruning
- Retains optimality and completeness

## Monte Carlo Tree Search

- Builds an imbalanced tree that prioritises more promising actions
- Takes many samples of games of random actions and can find a probability estimate of winning
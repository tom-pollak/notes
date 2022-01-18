---
date created: 2021-11-12 11:18

---

# Adversarial Search

## Game Tree

> Can be used to map out every different route our game can take

Solution in a form $(P1, (P2_1, P2_2))$
Can find the solution to maximize outcome with best possible response

## MaxMin Strategy

> Maximize Minimum Gain

- If we don't know the strategy the other agent will use, we need to **ensure** we get the highest payoff
- Consists of taking actions which maximize the worst-case utility for us
- Raises lower-bound for this game

## MinMax Strategy

> Minimize Maximum Payoff

- We can apply this same strategy to our opponent, to **minimize their maximum payoff**
  - In zero-sum, this is equivalent to minimising our maximum loss
- This lowers the upper-bound of our opponent's payoff for this game

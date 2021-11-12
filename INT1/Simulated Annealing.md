---
date created: 2021-11-12 10:25
date updated: 2021-11-12 11:18

---

# Simulated Annealing

Example of [[Local Search]]

**Annealing:** Mechanism which we can minimize energy

> **Simulated Annealing:** Metaheuristic optimisation algorithm which treats fitness of solution as energy of the system

## Boltzmann Distribution

> Describes probability of being in state $i$ with energy $E_i$

> $P_T(X=i) = \frac{e^{\frac{-E_i}{kT}}}{\sum_{j} e^{\frac{-E_j}{kT}}}$
>
> - $k$: Boltzmann constant
> - $T$: Temperatiure

- We can occasionally jump to a random point in space which has worse fitness
- As temperature decreases, this happens less often

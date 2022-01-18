---
date created: 2021-10-18 13:56
date updated: 2021-11-04 13:27

---

# Turing Machines

- Type 1 in [[Chomsky hierarchy]]

> ###### 5-tuple $(Q, \Sigma, \Gamma, q_0, \delta)$
>
> - $Q$: Set of finite states
>
> $\Sigma$: Input alphabet
> $\Gamma$: Tape alphabet, including blank symbol $\Delta$ where $\Sigma \subseteq \Gamma - \{\Delta\}$
> $q_0$: Input state
> $\delta: (Q - \{h_a, h_r\}) \times \Gamma \rightarrow Q \times \Gamma \times \{L, R, S\}$
> $h_a,\ h_r$: Halting states

## Configuration

> ##### $uqv$ where the tape is $uv$ and state $q$
>
> - The head reads the first symbol $v$
> - Head on symbol to right of state

## Transition

> ##### $\delta(q, a) = (r, b, R)$
>
> State $q \rightarrow r$
> Overwrites $a$ with $b$
> Moves head right

- Machine can crash if tape is not infinite in one direction and moves off the end
  - In this case it moves to halting reject state

- If there is no transition for some pair $(q,a)$ then $\delta(q,a) = (h_r, a, S)$
  - It rejects

## Acceptance

> #### Language is accepted by TM M
>
> ###### $L(M) = \{w \in \Sigma^*\ |\ q_0 \Delta w \vdash^* uh_av\ for\ some\ u,v \in \Gamma^*\}$

### Decision Problem

> Takes input a formula of first-order logic and decides if formula is universally valid

- Negatively answered by Alan Turing who coined an _algorithm_

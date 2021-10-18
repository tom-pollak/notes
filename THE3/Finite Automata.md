---
date created: 2021-10-18 13:55

---

# Finite Automata

> ###### 5 tuple $M = (Q, \Sigma, q_0, A, \delta)$
>
> - $Q$: Finite set of states
> - $\Sigma$: Input alphabet
> - $q_0 \in Q$: initial state
> - $A \subseteq Q$: Set of accepting states
> - $\delta: Q \times \Sigma \rightarrow Q$: Transition function

> ##### Extended transition function: $\delta^*: Q \times \Sigma^*  \rightarrow Q$
>
> ###### 1. $\delta^*(q, \Lambda) = q$ for $q \in Q$
>
> ###### 2. $\delta^*(q, wa) = \delta(\delta^*(q, w), a)$ for $q \in Q$ and $a \in \Sigma$
>
> > A **string** is accepted by $M$ if $\delta^*(q_0,w) \in A$.
> > The **language** accepted by $M$ is $L(M) = \{w \in \Sigma^*\ |\ w\ is\ accepted\ by\ M\}$

---
date created: 2021-10-18 13:56

---

# Nondeterministic Finite Automata

> Defined like [[Finite Automata | FA]], except for transition function:
>
> ###### $\delta: Q \times \Sigma \rightarrow 2^Q$ ($2^Q$ is power set)
>
> - Have the same [[Chomsky hierarchy]] as [[Finite Automata | FA]]

> ##### Extended transition function:
>
> ###### 1. $\delta^*(q, \Lambda) = \{q\}$ for $q \in Q$
>
> ###### 2. $\delta^*(q, wa) =  \bigcup_{p \in \delta^*(q, w)}\delta(p, a)$ for $q \in Q,\ w \in \Sigma^*\ and\ a \in \Sigma$
>
> > A **string** is accepted by NFA $M$ if $\delta^*(q_0,w) \cap A \neq \emptyset$.
> > The **language** accepted by $M$ is $L(M) = \{w \in \Sigma^*\ |\ w\ is\ accepted\ by\ M\}$

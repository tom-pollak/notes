# Pushdown Automata
> ###### 6-tuple $M = (Q, \Sigma, \Gamma, q_0, A, \delta)$
> - Q: Finite set of states (including $q_0$)
> - $\Sigma$: Input alphabet
> - $\Gamma$: **Stack alphabet**
> - $A \subseteq Q$: Set of accepting states
> - $\delta: Q \times (\Sigma \cup \{\Lambda\}) \times (\Gamma \cup \{\Lambda\}) \rightarrow 2^{Q \times (\Gamma \cup \{\Lambda\})}$
>    - Can make $\Lambda$ transitions

## Configuration
###### Triple tuple $(q, w, s)$
- $q$: State
- $w \in \Sigma^*$: Remaining input
- $s \in \Gamma^*$: Stack

## Transition

- $(q, av, As) \vdash (r, v, Bs)$ can take place if $(r, B) \in \delta(q, a, A)$
- State $q \rightarrow r$
- First symbol $a$ of input read
- Top of stack popped and changes $A \rightarrow B$

## Acceptance
> ###### $L(M) = \{w \in \Sigma^*\ |\ (q_0, w, \Lambda) \vdash^* (q, \Lambda, \Lambda)\ for\ some\ q \in A\}$
> - Empty string
> - Accepting state **or** empty stack

## [[Chomsky hierarchy#context-free]]
> ##### Language context-free iff accepted by some PDA
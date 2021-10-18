# Chomsky hierarchy

| Type | Grammars/ Languages        | Grammar productions                                                                           | Machines |
| ---- | -------------------------- | --------------------------------------------------------------------------------------------- | -------- |
| 0    | Unrestricted               | $\alpha \rightarrow \beta$ <br> $[\alpha \in (V \cup \Sigma)^+, \beta \in (V \cup \Sigma)^*]$ | [[Turing Machine]]     |
| 1    | [[Grammars#Context-sensitive]]   | $\alpha$ &rarr; $\beta$ <br> α ∈ (V ∪ Σ)+, \|α\| ≤ \|β\|]                                     | [[Linear-bounded Automata]]    |
| 2    | [[Grammars#Context-sensitive]]   | $A → β$ <br> $[A ∈ V, β ∈ (V ∪ Σ)∗]$                                                          | [[Pushdown Automata]]    |
| 3    | [[Languages#Regular Languages]] | $A \rightarrow aB,\ A \rightarrow \Lambda$ <br> $[A, B \in V, a \in \Sigma]$                  | [[Finite Automata]]     |

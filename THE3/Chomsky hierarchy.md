# Chomsky hierarchy

| Type | Grammars/ Languages        | Grammar productions                                                                           | Machines |
| ---- | -------------------------- | --------------------------------------------------------------------------------------------- | -------- |
| 0    | Unrestricted               | $\alpha \rightarrow \beta$ <br> $[\alpha \in (V \cup \Sigma)^+, \beta \in (V \cup \Sigma)^*]$ | [[TM]]     |
| 1    | [[Grammars#Context-sensitive]]   | $\alpha$ &rarr; $\beta$ <br> α ∈ (V ∪ Σ)+, \|α\| ≤ \|β\|]                                     | [[LBA]]    |
| 2    | [[Grammars#Context-sensitive]]   | $A → β$ <br> $[A ∈ V, β ∈ (V ∪ Σ)∗]$                                                          | [[PDA]]    |
| 3    | [[Languages#Regular Languages]] | $A \rightarrow aB,\ A \rightarrow \Lambda$ <br> $[A, B \in V, a \in \Sigma]$                  | [[FA]]     |

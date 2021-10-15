# Chomsky hierarchy

| Type | Grammars/ Languages | Grammar productions                                       | Machines |
| ---- | ------------------- | --------------------------------------------------------- | -------- |
| 0    | Unrestricted        | $\alpha$ &rarr; $\beta$ <br> α ∈ (V ∪ Σ)+, β ∈ (V ∪ Σ)∗]  | [[TM]]   |
| 1    | Context-Sensitive   | $\alpha$ &rarr; $\beta$ <br> α ∈ (V ∪ Σ)+, \|α\| ≤ \|β\|] | [[LBA]]  |
| 2    | Context-free        | $A → β$ <br> $[A ∈ V, β ∈ (V ∪ Σ)∗$                       | [[PDA]]  |

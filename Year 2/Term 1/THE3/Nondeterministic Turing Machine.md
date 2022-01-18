---
date created: 2021-10-18 13:56

---

# Nondeterministic Turing Machine

> Defined simiarly to [[Turing Machine | TM]], except:
>
> #### Transition function: $δ : (Q − {h_a}) × Γ → 2^{Q×Γ×\{L, R, S\}}$
>
> ##### No reject state (as multiple paths)

- Given δ(q, a) = ∅, NTM halts without acceptance or rejection
- If NTM loops, string may or may not be in language
- For any NTM N, there exists a [[Turing Machine | TM]] such that L(N) = L(D)

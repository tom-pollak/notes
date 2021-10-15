# Nondeterministic Turing Machines
> Defined simiarly to [[TM]], except:
> #### Transition function: $δ : (Q − {h_a}) × Γ → 2^{Q×Γ×\{L, R, S\}}$
> ##### No reject state (as multiple paths)

- Given δ(q, a) = ∅, NTM halts without acceptance or rejection
- If NTM loops, string may or may not be in language
- For any NTM N, there exists a [[TM]] such that L(N) = L(D)
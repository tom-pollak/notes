# Multitape Turing Machine

> Defined simiarly to [[Turing Machine | TM]] except:
> ##### $δ : (Q − {h_a, h_r}) × Γ ^ n → Q × Γ n × \{L, R, S\}^n$
> where $n \geq 2$

- Configuration is a n-tuple $(u_1qv_1, u_2qv_2, ...)$

## Enumerating languages
> Can be used for [[Languages#Semidecidable Languages | Semidecidable languages]]

###### Can enumerate language L if:
1. Computation begins with all tapes blank
2. Tape head on tape 1 never moves left
	- Tape 1 is output tape
3. At each point in computation, contents of tape 1 has form: 
	- $∆ \#w_1 \#w_2\# ... \#w_n\#v$, where $n ≥ 0, w_i ∈ L, \# ∈ (Γ − Σ)$ and $v ∈ Σ^∗$
	- **Soundness: every string listed belongs to L**
4. Every $w∈L$ will eventually appear as one of the strings $w_i$ on tape 1
	- **Completeness: every string in L will eventually be listed, may contain repeating strings**
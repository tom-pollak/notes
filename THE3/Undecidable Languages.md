---
date created: 2021-11-03 16:10
date updated: 2021-11-04 13:27

---

# Undecidable languages

## Self Accepting

> Define $SA \subseteq \{0,1\}^*$ (**self-accepting**) by
>
> - $SA = \{e(M)\ |\ M\ is\ a\ TM\ and\ e(M) \in L(M)\}$
>
> And let $NSA = \overline{SA}$ (**non-self-accepting**)

- $SA$ consists of codes of all [[Turing Machine | TM]] that accept their own codes

> $NSA$ is not [[Semidecidable Languages| Semidecidable]] — contradiction proof
>
> - By consequence, $SA$ is not decidable ([[Decidable Languages#Complement]])
> - However, $SA$ is [[Semidecidable Languages| Semidecidable]]

## Universal Turing Machine

> Universal TM $U$ takes inputs of form $e(M)e(w)$ where $M$ is a TM and $w$ is a sting over $M's$ input alphabet

Machine $U$ simulates $M$ on input $w$

- accepts if $M$ accepts $w$
- rejects if $M$ rejects $w$
- diverges (loops) if $M$ diverges from $w$

Hence $U$ is an interpreter for TMs

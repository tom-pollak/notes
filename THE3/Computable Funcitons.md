---
date created: 2021-11-03 17:01
date updated: 2021-11-03 17:08

---

# Computable Functions

## Turing computable functions

> A [[Turing Machine]] computes the partial function $f_M: \Sigma^* \rightarrow \Sigma^*$ defined by
> $f_M(x) = \lbrace$ if $y\ \ \ \ \ \ \ \ \ \ \ \ \ \ q_0\Delta x \vdash^*h_a\Delta y$ for some $y \in \Sigma^*$
> $\ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \lbrace undefined \ \ \ otherwise$

- A partial function is Turing-computable (computable) if exists a TM $M$ such that $f_M=f$

<br>

$f_M(x)$ is undefined if:

- $M$ diverges
- $M$ halts in state $h_r$
- $M$ halts with head not on square 1
- $M$ halts with a non-blank symbol on square 1
- $M$ halts with symbol on tape that is not in $\Sigma \cup \{\Delta \}$
- $M$ halts in configuration $h_a \Delta v$ whre $v$ contains non-blank symbol

## Characteristic function of a language
For every alphabet $\Sigma$, fix distinct strings $w_1, w_2 \in \Sigma^*$. The **characteristic function** of a language  is the function
>$\chi_L: \Sigma^* \rightarrow \Sigma^*$ defined by:
>>
>> $\chi_L(x) = \lbrace\ w_1\ \ if\ x \in L,$
>> $\ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \ \lbrace\ w_2\ \ otherwise$

$\chi_L$ is a total function, hence TM computing will accept every input and produce $w_1$ or $w_2$ on the tape

> A language $L$ is decidable iff characteristic function $\chi_L$ is computable



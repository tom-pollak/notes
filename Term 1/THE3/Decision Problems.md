---
date created: 2021-11-04 11:42
date updated: 2021-11-04 11:53

---

# Decision Problems

> **Set of questions**, each of which have the answer yes or no
>
> Questions are _instances_ of the decision problem; depending on their answers, they are either yes-instances or no-instances

## Encoding decision problems as languages

Solve a decision problem $P$ by [[Turing Machine]], instances $I$ are encoded as strings $enc(I)$ over some alphabet $\Sigma$

- $Y(P)$ — language of encoded yes instances
- $N(P)$ — language of encoded no instances
- $E(P) = Y(P) \cup N(P)$ — all encoded instances

Encoding $enc$ is reasonable if:

- $Y(P) \cap N(P) = \emptyset$
- $E(P)$ is decidable
- There is a decoding algorithm which given a code $w \in E(P)$ construncts an instance $I$ such that $enc(I) = w$

> Decision problem $P$ is only [[Decidable Languages |decidable]] if $Y(P)$ is decidable
> [[Semidecidable Languages |Semidecidable]] if $Y(P)$ is semidecidable

### Membership Problem

Membership problem for [[Regular Languages]]
Input: A [[Finite Automata]] $M$ and $w \in \Sigma^*$
Question: Is $w \in L(M)$?

Problem domain: $D = \lbrace (M, w)\ |\ M\ is\ a\ FA\ and\ w \in \Sigma^*\rbrace$

Yes-instances: $\lbrace (M, w) \in D\ |\ w \in L(M) \rbrace$
No-instances: $\lbrace (M, w) \in D\ |\ w \notin L(M) \rbrace$

<br>

**Decidable problem:**
TM deciding this first checks if its input $x$ is in $E(P)$ (and rejects if not), decodes $x$ into [[Finite Automata | FA]] $M$ and a string $w \in \Sigma^*$, and runs $M$ on input $w$.

TM accepts $x$ iff $M$ accepts $w$

## Complement

> $\overline{P}$ is obtained by swapping yes and no

- If $P$ is decidable, then its complement is also decidable
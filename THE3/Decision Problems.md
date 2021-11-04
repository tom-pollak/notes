---
date created: 2021-11-04 11:42

---

# Decision Problems

> **Set of questions**, each of which have the answer yes or no
>
> Questions are _instances_ of the decision problem; depending on their answers they are either yes-instances or no-instancees

##### Example

Membership problem for regular languages
Input: A finite automaton $M$ and $w \in \Sigma^*$
Question: Is $w \in L(M)$

Problem domain: $D = \lbrace (M, w)\ |\ M\ is\ a\ FA\ and\ w \in \Sigma^*\rbrace$

Yes-instances: $\lbrace (M, w) \in D\ |\ w \in L(M) \rbrace$
No-instances: $\lbrace (M, w) \in D\ |\ w \notin L(M) \rbrace$


## Encoding decision problems as languages

Solve a decision problem $P$ by TMs, instances $I$ are encoded as strings $enc(I)$ over some alphabet $\Sigma$
- $Y(P)$ — language of encoded yes instances
- $N(P)$ — language of encoded no instances
- $E(P) = Y(P) \cup N(P)$ — all encoded instances

Encoding $enc$ is reasonable if:
- $Y(P) \cap N(P) = \emptyset$
- $E(P)$ is decidable
- There is a decoding algorithm which given a code $w \in E(P)$ construncts an instance $I$ such that $enc(I) = w$
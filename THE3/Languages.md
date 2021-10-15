# Languages
> ###### Alphabet: non-empty finite set ($\Sigma$ or $\Gamma$) of symbols
> ###### String: sequence of symbols over an alphabet $\Sigma$
	>> Empty String: $\Lambda$
	>> Length: $|w|$
	>> Set of all strings: $\Sigma^*$
	>> Formal language over $\Sigma$: Subset of $\Sigma^*$

> ###### Concatenation of languages:
> For $L_1,\ L_2 \subseteq \Sigma^*$,
> 
> $L_1L_2 = \{uv\ |\ u \in L_1\ and\ v \in L_2\}$

# Regular Languages (RL)

### Inductive Definition

1.  Empty set $\emptyset$ and $\{a\}$ for each a in $\Sigma$, are RL over $\Sigma$
2.  If $L_1$ and $L_2$ are RL over $\Sigma$:
	- > $L_1 \cup L_2$ and $L_1L_2$ and $L^*$

# Decidable Languages

### Language Definition
> ###### Language L is decidable (recursive) if accepted by some [[TM]] M that on every input eventually reaches a halting configuration
>>######  M Decides L

### Machine Definition
> ###### Given a string $w ∈ Σ^*$, run M on W until M reaches halting configuration: then $w∈L$ iff M is in state $h_a$

- Context-sensitive $\implies$ decidable

## Crash Avoidance
> ###### For every TM $M$ there is a TM $M'$ such that $L(M) = L(M')$ and $M'$ does not crash on any input

We extend $\Gamma$ with a new symbol $\#$. Machine $M'$ writes $\#$ on the first square, inserts $\Delta$ on the 2nd square by shifting input string one position to the right, moves tape head to 2nd square, and then executes the transitions of $M$. We also define, for each:

> $q \in Q' - \{h_a, h_r\},\ \delta'(q,\#) = (h_r,\#,S)$.

## Complement
> ###### If language L is decidable, then its complement $\overline{L} = \Sigma^* - L$ is also decidable

Let $M$ be a TM that accepts $L$ and halts on every input. Without loss of generality, we assume $M$ never crashes at the start of the tape. We modify $M$ to a machine $\overline{M}$ by swapping accept and reject states, defined as:

> $\overline{h_a} = h_r$ and $\overline{h_r} = h_a$

Then $L(\overline{M}) = \overline{L}$. Moreover, $\overline{M}$ halts on every input as M does so. Hence $\overline{L}$ is decidable.

# Semidecidable Languages

> ###### Language L is semidecidable (or recursively enumerable) if there exists a [[TM]] that accepts L
> ###### Type 0

## Semidecidable → decidable
> ###### If both a language $L$ and its complement $\overline{L}$ are semidecidable, then $L$ is decidable.
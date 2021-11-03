# Decidable Languages

### Language Definition

> ###### Language L is decidable (recursive) if accepted by some [[Turing Machine | TM]] M that on every input eventually reaches a halting configuration
>
> > ###### M Decides L

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
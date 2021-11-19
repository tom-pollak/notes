---
date created: 2021-11-19 16:57
date updated: 2021-11-19 17:15

---

# First-Order Logic

In [[Propositional Logic]], we couldn't represent **general** dynamics of the world.

- E.g. It's breezy iff there is a pit adjacent: must be represented by $\vee$ every adjacent square.

- Atomic Sentence: State fact about the world

- Term: Variables and constants
  - Allowed to use **unbound** literals & variables, such as:
    - $King(x) \implies Person(x)$, $Sibling(James, x) \implies Sibling(x, James)$

- Universal quantifiers: Can define sentences that apply across multiple instantiations of a variable:
  - $\forall x\ King(x) \implies Person(x)$
  - $\forall x \forall y\ Sibling(x, y) \iff Sibling(x, y)$

- Existential Quantifiers: Existence of a true instance:
  - $\exists x\ King(x) \vee Queen(x)$ — There exists some $x$ such that $x$ is a king or a queen
  - $\forall x \exists y\ Loves(x, y)$ — Everybody loves somebody
  - $\exists y \forall x\ Loves(x, y)$ — Someone that everybody loves

## Substitution

### Tell and Ask

- $Tell(KB, King(John))$
- $Tell(KB, \forall x\ King(x) \implies Person(x))$

<br>

- $Ask(KB, King(John))$
- $Ask(KB, Person(John))$

However, not all queries make sense:

- $Ask(KB, \exists x\ Person(x))$ will return true if a person exists

We need a **substitution** $x$ to satisfy query

### Definition

- Function that maps variables to terms

Example

- Formula $e = Likes(x, y)$ where neither variable is bound to any quantifier
- Substitution $\theta = \lbrace x/James,\ y/Beer \rbrace$
- Applying $\theta$ to $e$ gives:
  - $\theta (e) = Likes(James,  Beer)$

Formally:

> Restricted finite set of replacements, each one of which takes the form $\{x/t\}$ where $x$ is a variable and $t$ is a term

Non-empty substitution form: $\theta = \lbrace x_1/t_1, x_2/t_2, \ldots, x_n/t_n \rbrace$

- Application of a substitution $\theta$ to any formula $e$ is the act of **simultaneously** replacing for all $i \in \lbrace 1,2, \ldots, x_n/t_n \rbrace$, every **free** occurrence of $x_i$ in $e$ with $t_i$

### Terminology

- **Expression:** $e$
- **Instance:** $\theta(e)$
- **Ground:** expression ($e$) iff contains no free variables
- **Ground Instance**
- $e_{gr}$: Set of all ground instances of $e$
- $E$: Set of expressions, $E_{gr}$: set of all ground instances

## Inference




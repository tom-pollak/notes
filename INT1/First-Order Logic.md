---
date created: 2021-11-19 16:57
date updated: 2021-11-21 20:52

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

> **Propositionalisation:**

### Existential Elimination

Can produce a **new** constant and replace variable by that new constant

$\exists x\ Crown(x) \wedge OnHead(x, John)$

Is replaced by:
$Crown(C_1) \wedge OnHead(C_1, John)$

### Universal Instantiation

Add a new sentence for each ground term in KB:

$\forall x\ King(x) \wedge Greedy(x) \implies Evil(x)$

becomes:
$King(John) \wedge Greedy(John) \implies Evil(John)$
$King(Richard) \wedge Greedy(Richard) \implies Evil(Richard)$

### Modus Ponens

For atomic sentences $p_i, p'_i, q$ and some substitution $\theta$ such that $Subst(\theta, p'_i) = Subst(\theta, p_i)$

$p'_1, \ldots, p'_n\ \ \ \ (p_1 \wedge \ldots \wedge p_n \implies q)$
--------------------
$Subst(\theta, q)$

#### Unification

> Finding suitable substitution such that different logical expressions look identical

## Chaining

### Forward Chaining

1. Start with ground terms
2. Combine rules to generate new terms
	- Brute force rule combinations

### Backward Chaining

1. Start with query
2. Apply rules recursively until we get to ground terms
	- Use unification with substitutions
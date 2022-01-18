---
date created: 2021-11-12 10:25

---

# Population-based techniques

Example of [[Local Search]]

> Maintain a number of different solutions at the same time

- Can have interesting effects if we have solutions that interact

## Genetic Algorithms

> Maintain a population of individuals. Each generation population replaced with new individuals that are either copies of, offspring from, or mutated forms of previous population.

- Encode a solution in **genotype** — often bitstring
  - Humans it is DNA
- Genotype makes mutation easier
- Genotype converted in phenotype to determine its fitness
  - Phenotype is a human

### Crossover

> Implement “mating” of binary strings

- Could split the genotype in two, create two binary strings with each of the four halves, then maximize


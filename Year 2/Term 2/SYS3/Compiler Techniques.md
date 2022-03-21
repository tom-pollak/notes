---
date created: 2022-03-21 19:36
date updated: 2022-03-21 21:31
---

# Compiler Techniques

## Instruction level parallelism

(ILP)

- Pipelining overlaps execution of instructions

- Compiler-based static approaches

- Hardware-based dynamic approaches

Goal of exploiting ILP: Minimizing [[Principles of Computer Design#CPU Time |CPI]]
$\small \text{Pipeline CPI} = \text{Ideal (based) CPI} + \text{Structural stalls} + \text{Data hazards stalls} + \text{Control stalls}$

## Basic block

> Straight-line code sequence without branches (except entry & exit)

- Parallelism limited

![[building-basic-blocks.png]]

- Leaders: Start of basic block
- Performance gains optimising instruction level in basic blocks is limited

## Dependence

### Data dependence

- Loop-level parallelism
  - Unroll loop statically or dynamically
- Data dependence conveys possibility of a hazard
- Dependant instructions cannot be executed simultaneously

### Name dependence

> Two instructions use same name but no flow of information

- Not a true data dependence, but problem when reordering instructions

![[name-dependence.png | 300]]

### Antidependence

> Instruction $j$ writes to a register or memory location that instruction $i$ reads

- Initial ordering ($i$ before $j$) must be preserved

### Output dependence

> Instruction $i$ & $j$ write the same register or memory location

- Ordering must be preserved

### Control dependence

> Ordering of instruction with respect to a branch

- An instruction that is control dependent on a branch cannot be moved **before** the branch
  - So that its execution no longer controlled by the branch
- Instruction that is not control dependent on the branch cannot be moved **after** the branch
  - So that its execution controlled by the branch

## Loop unrolling & scheduling

- Identify independency of loop iterations
- Use different registers to avoid unnecessary constraints put in on same computations
- Eliminate the extra test and branch instructions and adjust loop termination and iteration code
- Determine whether the loads and stores of different iterations are independent
- Schedule the code, preserving any dependences needed to yield the same result as original code

### Strip mining

> Unroll loop with unknown number of loop iterations

- Goal: make $k$ copies of loop body (Num iterations = $n$)
- Generate a pair of loops
  - execute $n \text{ mod } k$ times
  - execute $\frac{n}{k}$ times
- E.g. Let $n=35, k=4$
  - Loop 1 executes 3 times $35 \text{ mod } 4 = 3$
  - Loop 2 executes 8 times by unrolling 4 copies per iteration.

### Limitations of loop unrolling

- Code size limitations: I-cache miss
  - Size of program increases requires more cache
- Compiler limitations: register pressure

---
date created: 2022-03-18 12:46
date updated: 2022-03-18 13:05
---

# Dynamic Scheduling

```
> Rearrange execution order of instructions
```

- Reduce stalls while maintaining data flow
- Compiler doesn't need to know microarchitecture
- Handles cases where dependencies are unknown at compile time

Disadvantages:

- Substantial increase in hardware complexity
- Complicates exceptions

In a simple pipeline, if instruction $j$ depends on long-running instruction $i$, then all instructions after $j$ must be stalled until $i$ is finished and $j$ can execute.

## How dynamic scheduling works

- Separate the issue process into two parts
  - Checking for structural hazards
  - Waiting for the absence of a data hazard
- Use in-order instruction issue but want instruction to begin execution as soon as its data operands are available
- Out-of-Order execution $\rightarrow$ Out-of-Order completion
- Out-of-Order execution introduces WAR and WAW hazards

![[WAR-WAW-hazards.png|300]]

WAR & WAW hazards – solved by register renaming

Possibility of imprecise exception

- Pipeline may complete instructions that are later in program order than the instruction that causes the exception
- Pipeline may have not yet completed instructions earlier in the program order than the instruction causing the exception
- Usually have to rollback all instruction after the exception and ensure the instructions before the exception are complete

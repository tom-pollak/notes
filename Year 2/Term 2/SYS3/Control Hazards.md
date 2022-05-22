---
date created: 2022-02-14 14:11
date updated: 2022-02-14 15:25
---

# Control Hazards

## Control Hazard on Branches

- In a normal pipeline, branching happens at the 4th stage
  - If the branch is wrong, the pipeline must flush the 3 invalid subsequent instructions
- In a branch optimized 5 stage pipelines, branching is done in the 2nd stage
  - Only necessary to flush one instruction, much easier
    - Branch is a test on 0 can be done before the ALU as all it does is check whether the value is 0

![[5-stage-branch-optimized.png]]

## Branch Prediction

### Stall until branch direction is clear

### Predict Branch Not Taken

- Execute successor instructions in sequence
- “Squash” instruction pipeline if branch actually taken

### Predict Branch Taken

- Branch address is not known by IF stage
- Target known same time as branch outcome
- 1 cycle branch penalty will be incurred

### Delayed Branch

- Define branch to take place AFTER one instruction following branch instruction
- 1 slot delay allows proper decision and branch target address in 5 stage pipelines
- **Where to get instructions to fill branch delay slot?**
  - Find instruction that is executed whether or not branch is taken

#### Filling branch delay slot

![[filling-branch-delay.png]]

## Dynamic Branch Prediction

Execution of a branch requires knowledge of:

- Branch instruction: encode whether an instruction is a branch or not
  - Decide on taken or not taken
- If branch is taken what is the target address
  - Can be computed but can also be precomputed i.e. stored in a table
- If branch is taken what is the instruction at branch target address
  - Saves fetch cycle for that instruction

### Branch prediction buffer

- Or a branch prediction table (BPT), branch history table (BHT)
  - Records previous outcomes of the branch instruction
  - How to index table is an issue
- Prediction using BPB is attempted when the branch instruction is fetched (IF stage)

- Acted upon during ID stage

Has a prediction been made

- If not use default 'Not taken'

Is it correct or incorrect

- Correct (most cases): no delay
- Incorrect: delay

#### Prediction Scheme with 1 or 2 bit FSM

![[prediction-fsm.png]]

- Allow branches that favour taken/not-taken to be mispredicted less often

- **Branch prediction extremely useful in loops**

- Simple branch prediction can be implemented using a small amount of memory indexed by lower order bits of the address of the branch instruction
  - One bit stores whether the branch was taken or not
  - Next time branch instruction fetched refer this bit

#### Correlating predictor

```java
if (x == 2) x = 0; /* br-1 */
if (y == 2) y = 0; /* br-2 */
if (x != y) do this; /* br-3 */
else dot that; /* br-4 */
```

- Multiple 2-bit predictors for each branch
- One for each possible combination of outcomes of **preceding n branches**

#### Local predictor

- Multiple 2-bit predictors for each branch
- One for each possible combination of outcomes for the **last n occurrences of this branch**
  - So compare to the outcome of the last time the branch was called

#### Tournament predictor

- Combine correlating and local predictor

### Branch-target buffer

> Branch prediction cache, that stores the predicted address for the next instruction after branch

- To reduce the branch penalty, know whether the next undecoded instruction is a branch
  - If so what the next PC should be
- If the instruction is a branch, and we know what PC should be, we can have a branch penalty of 0

![[branch-target-buffer.png]]

#### Branch folding

> Optimization on [[Control Hazards#Branch-target buffer | BTB]] to make a zero cycle branch

- Larger BTB: store one or more target instructions
- Add target instruction into BTB to deal with longer decoding time required by larger buffer
- Can be used to obtain 0-cycle unconditional branches and sometimes 0-cycle conditional branches

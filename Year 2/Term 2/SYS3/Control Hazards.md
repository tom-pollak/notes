F---
date created: 2022-02-14 14:11
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
- "Squash" instruction pipeline if branch actually taken


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
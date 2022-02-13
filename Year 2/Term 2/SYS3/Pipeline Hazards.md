---
date created: 2022-02-13 17:57
---

# Pipeline Hazards

## Limits

> **Hazards:** Circumstances that would cause incorrect execution if next instruction is fetched and executed

- **Structural:** Different instructions at different stages in the pipeline want to use the same hardware resource
- **Data:** An instruction in pipeline requires data to be computed by a previous instruction still in pipeline
- **Control:** Succeeding instruction to put into pipeline depends on outcome of a previous branch instruction already in pipeline

### Structural

![[Structural Hazard.png]]

Solutions:

- Wait
  - Must detect hazard
  - Must have mechanism to stall
- Duplicate hardware
  - Multiple units will help both instructions progress

![[Different instruction and data cache.png]]

- Using a different cache for instructions and data will mitigate the writeback issues when an instruction is trying to read while another instruction is trying to write

### Data
> Reading an old version of data from the writeback not being called yet

#### Read After Write

- Instruction tries to read operand before previous instruction write it

#### Write After Read

- Instruction writes operand before instruction reads it
- Called anti-dependance by compiler writers
- Can't happen in 5 stage pipelines as all instructions take 5 stages and reads are always stage 2 while writes are always stage 5

#### 
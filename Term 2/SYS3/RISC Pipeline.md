---

date created: 2022-02-14 14:02
---

# RISC Pipeline

## MIPS

> Microprocessor without Interlocked Pipelined Stages

- 32 registers, 32 bits each
- Uniform length instructions
- RISC Load-store architecture

## Pipeline Characteristics

- Doesn't reduce latency of single task, improves throughput of entire workload
- Pipeline rate limited by slowest pipeline stage
- Potential speedup = Number of pipe stages

Reducing speedup Factors

- Unbalanced lengths of pipe stages
- Time to fill and drain pipeline

## Pipelining in Circuits

- Pipelining system into multiple independent stages with added buffers between the stages

![[Pipelining in Circuits.png]]

## Pipelined RISC Data Path

![[Pipelined RISC Data Path.png]]

- Every unit at the beginning of the clock cycle will accept the input from the input pipeline register to perform execution and then output the result in the output pipeline register which will be used by the next unit.
- Branch instructions: 4 cycles
- Store instructions: 4 cycles
- Any other instructions: 5 cycles

### Instruction Fetch

- Based on PC, fetch instruction from memory
- Increment PC

### Instruction decode

- Register fetch cycle
- Decode instruction & register read operations

### Execution

> Effective address cycle (EX)

- Memory reference: Calculate effective address
  - [LW R1, 8 (R2)] which has an effective address: [R2] + 8

### Memory Access Cycle

- Load from memory and store in register or vice versa

### Write-back

- Any write operation to be stored in a register
- Writing result back to register

## Pipelining Issues

> ISA: (Industry Standard Architecture) An ISA bus provides a basic route for peripheral devices that are attached to a motherboard to communicate with different circuits

### Ideal case: Uniform sub-computations

- Computation to be performed can be evenly partitioned into uniform-latency sub-computations

Reality: Internal fragmentation

- Not all pipeline stages may have uniform latencies

Impact of ISA:

- Memory access is a critical sub-computation
- Memory addressing modes should be minimized
- Fast cache memories should be employed

### Ideal case: Identical computations

- Same computation is to be performed repeatedly on many input data sets

Reality: External fragmentation

- Some pipeline stages may not be used

Impact of ISA:

- Reduce complexity and diversity of instruction types
- RISC architectures use uniform stage simple instructions

### Ideal case: Independent computations

- All instructions are mutually independent

Reality: Pipeline stalls – cannot proceed

- A later computation may require result of an earlier computation

Impact of ISA

- Reduce memory addressing modes - dependency detection
- Use register addressing mode – easy dependencies check

Easier to detect dependency
ADD R1, R2, R3
SUB R4, R1, R5

Hard to detect dependency
SW R6, 16(R1)
LW R8, 8(R2)

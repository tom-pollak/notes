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




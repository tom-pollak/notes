---
date created: 2022-01-26 18:51
date updated: 2022-01-26 18:58

---

# Principles of Computer Design

## Measuring Performance

- Response time
- Throughput
  - Transactions per unit time
- CPU time
- Wall clock time
  - Overall time taken
- Speedup
  - If execution time is faster than on program X than program Y

### Benchmarks

- Toy programs
  - Sorting
  - Matrix multiply
- Synthetic benchmarks
- Benchmark suites
	- SPEC06
	- SPLASH

#### Benchmark Evaluation

- IPC – Instructions per cycle
- Instruction profile
	- Type of instructions executed
- L1 data cache misses per 1000
- Branch mispredictions per 1000

#### SPEC Ratio

 - Reference for SPEC 2006: Sun Ultra Enterprise 2 workstation with a 296-MHz UltraSPARC II processor

$SPECRatio_A = \frac{\text{Executioni time}_{reference}}{\text{Execution time}_A}$

$\frac{SPECRatio_A}{SPECRatio_B} = \frac{Performance_A}{Performance_B}$


## Amdahl's Law

- Defines speedup that can be gained by improving some portion of a computer
	- Limited by the fraction of time the faster mode can be used

$\text{Execution time}_{new} = \text{Exection time}_{old} \times \left( (1 - \text{Fraction}_{enhanced}) + \frac{Fraction_{enhanced}}{Speedup_{enhanced}}\right)$

$\large Speedup_{overall} = \frac{\text{Execution time}_{old}}{\text{Execution time}_{new}} = \frac{1}{(1 - \text{Fraction}_{enhanced}) + \frac{Fraction_{enhanced}}{Speedup_{enhanced}}}$


## CPU Time

$\text{CPU time} = IC \times CPI \times CCT$

- Clock cycle time – hardware technology
- CPI – organization and ISA
- IC – ISA and compiler technology

Different instruction types may have different CPIs

$\text{CPU clock cycles} = \sum\limits_{i=1}^n IC \times CPI_i$
$\text{CPU time} = CCC \times CCT$


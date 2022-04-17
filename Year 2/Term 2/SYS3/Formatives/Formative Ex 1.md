# Ex 1

## 1

>Explain the difference between CISC and RISC processors. Name two processors that belong to  CISC and RISC.

A RISC processor uses a small set of instructions, all of the same length. These are simple and can be executed in one clock cycle. SPARC is an example of a RISC processor

A CISC processor uses instructions of variable sizes and can use a variety of addressing modes. An instruction can take longer than one clock cycle to complete.


## 2

>Distinguish between a memory-register instruction set (such as x86) and a load‐store instruction  set (such as MIPS). What are their relative performance advantages in today's technology?

An instruction that combines memory access with another operation.

A load store instruction can read and store data from main memory, but may take multiple clock cycles to perform the IO operation. However, it can read any data currently stored in the memory the computer

Memory register is advantageous where memory speed is fast relative to the processor. However, in todays world, memory access is much slower, so restricing mem access to specialized instructions allows the other operations to complete more quickly


## 3

>We wish to compare the performance of two different systems: S1 and S2. System S1 costs £10K  and System S2 costs £15K. The following measurements have been made on these systems:

| Program | Time on S1 | Time on S2 |
| ------- | ---------- | ---------- |
| 1       | 10 seconds | 5 seconds  |
| 2       | 3 seconds  | 4 seconds

### a 
>One user cares only about the performance of program 1. Given that cost effectiveness is measured in executions per second per pound, which machine is more cost effective for  running program 1? By how much?

$\text{cost effectiveness} = (executions / sec) / \$$ (Higher is better)

Program 1: $\frac{\frac{1}{10}}{10000}= \frac{1}{100000} (0.00001)$

Program 2: $\frac{\frac{1}{3}}{15000} =\frac{1}{45000} (2.2 \times 10^{-5})$

$\frac{1}{45000} > \frac{1}{100000} \therefore$ program 2 is more cost effective

### b

>Another user is concerned with throughput of the systems as measured with an equal workload of programs 1 and 2. Which system has better performance for this workload, given that performance is inversely proportional to execution time? By how much? Which system is more cost effective for this workload? By how much?


$\text{cost effectiveness} = avg(\text{cost effectiveness}_{S1}, \text{cost effectiveness}_{S2})$

$performance = \frac{1}{\text{execution time}}$

Performance (higher is better):

$\text{program 1: } \frac{\frac{1}{10} + \frac{1}{5}}{2} = 0.15$

$\text{program 2: } \frac{\frac{1}{3} + \frac{1}{5}}{2} = \frac{8}{30} = \frac{4}{15} = 0.26667$


### c

> Yet another user has the following requirements: Program 1 must be executed 200 times  each hour. Any remaining time can be used for running program 2. If the system has  enough performance to execute program 1 the required number of times per hour,  performance is measured by the number of executions per hour for program 2. Which  system has higher performance for this workload? Which is more cost effective?

Time taken to run S1 200 times:

Program 1: $200 \times 10 = \text{2000 seconds} = \text{55 minutes}$ = no

Program 2: $200 \times 3 = \text{600 seconds} = \text{10 minutes}$

## 5

>Suppose you wish to run a program P with7.5 × 10^9  instructions on a 5 GHz machine with a CPI  of 0.8.


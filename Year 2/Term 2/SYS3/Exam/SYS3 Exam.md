# SYS3 Exam
_Y3891128_

## Part 1

### 1.i

**False**

Data bus is bidirectional – processor can read and write data to and from memory.

Address bus is unidirectional – processor addressing a specific memory location, no device can write to the microprocessor.

### 1.ii

##### TODO

**True**

 **When reading from memory, data addressed by MAR is fed into the MDR (memory data register) and then used by the CPU**. When writing to memory, the CPU writes data from MDR to the memory location whose address is stored in MAR.

memory address register (MAR) - holds the address of the current instruction that is to be fetched from memory, or the address in memory to which data is to be transferred. memory data register (MDR) - holds the contents found at the address held in the MAR, or data which is to be transferred to primary memory.

### 1.iii

**False**

In a Load-Store Architecture, ALU operations only occur between registers.

![Load-Store Architecture - an overview | ScienceDirect Topics](https://ars.els-cdn.com/content/image/1-s2.0-B9780124202320000015-f01-18-9780124202320.jpg)

### 1.iv

**False**

Register renaming is used to resolve WAR & WAW hazards

## Part 2

### 2.i
##### TODO: Check equation correct

**Assumption:** The usability of $A$, $B$, and $C$ are mutually exclusive.

$$\small Speedup =
\frac{1}{ (1 - \text{Fraction}_{A} - \text{Fraction}_{B} - \text{Fraction}_{C})
	+ \frac{Fraction_{A}}{Speedup_{A}} + 
	+ \frac{Fraction_{B}}{Speedup_{B}} +
	+ \frac{Fraction_{C}}{Speedup_{C}} }
$$

$$8 =
\frac{1}{ (1 - 0.35 - 0.35 - x)
	+ \frac{0.35}{20} + 
	+ \frac{0.35}{30} +
	+ \frac{x}{25} }
$$
$\implies x = 0.2127\ (4.dp),\ (21\%)$


### 2.ii

	$Speedup_{A} = \frac{1}{(1-0.2) + \frac{0.2}{20}} = 1.23\ (2.dp)$
	$Speedup_{B} = \frac{1}{(1-0.2) + \frac{0.2}{30}} = 1.24\ (2.dp)$
	$Speedup_{C} = \frac{1}{(1-0.6) + \frac{0.6}{25}} = 2.36\ (2.dp)$

#### 2.ii.a

To achieve the highest performance, we must choose the enhancement that achieves the highest speedup.

Therefore, we implement enhancement $C$, with a speedup of $2.36$.

#### 2.ii.b

We implement the two enhancements with the highest speedups, $B$ (1.24) and $C$ (2.36)


### 2.iii

##### TODO

## Part 3

### 3.i

##### TODO: clean-up dependencies

|       | Instruction sequences                                       | Dependencies                                                                             |
| ----- | ----------------------------------------------------------- | ---------------------------------------------------------------------------------------- |
| **A** | 1. LW R1, 40(R6)<br>2. Add R6, R2, R2<br>3. SW R6,50(R1)    | RAW on R1 from Instruction 1 to Instruction 2<br>RAW on R1 from Instruction 1 to Instruction 3 |
| **B** | 1. LW R5, -16(R5)<br>2. SW R5, -16(R5)<br>3. ADD R5, R5, R5 | RAW on R5 from Instruction 1 to 1nstruction 2<br>RAW on R5 from Instruction

### 3.ii

### 3.iii

## Part 4

### 4.i

### 4.ii

## Part 5

### 5.i

### 5.ii

### 5.iii

## Part 6

### 6.i

### 6.ii

### 6.iii

### 6.iv

## Part 7

### 7.i

### 7.ii

### 7.iii
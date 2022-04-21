# Sys3 Open Assessment
---
**REMOVE**

A Data Hazard can occur when Instruction Fetch (IF) conflicts with a Data Fetch (DF), or data store (DS). This is due to the memory bus only being able to perform one code or data operation per clock cycle. A possible solution is to insert stalls to delay the second of the events and thus separate the conflicting operations into different clock cycles.

---

## Part A


### A(i)

| Hazard Type | 1st Instruction | 2nd Instruction |
| ----------- | --------------- | --------------- |
| RAW         | (1, 6, WB.3)      | (2, 5, RR.3)    |
| WAW         | (2, 8, WB.5)    | (3, 7, WB.5)    |
| WAW         | (4, 9, WB.2)    | (5, 8, WB.2)    |
| Structural  | (2, 8, WB.5)    | (5, 8, WB.2)    |
| Memory      | (2, 4, OF)      | (4, 4, IF)      |

### A(ii)

| Hazard Type | 1st Instruction | 2nd Instruction | 3rd Instruction |
| ----------- | --------------- | --------------- | --------------- |
| Memory      | (1, 3, OF)      | (3, 3, IF)      |                 |
| Memory      | (2, 4, OF)      | (4, 4, IF)      |                 |
| Structural  | (1, 7, IALU)    | (3, 7, IALU)    | (4, 7, IALU)    |
| Structural  | (3, 8, WB.5)    | (4, 8, WB.2)    |                 |
| WAR         | (1, 5, RR.3)    | (3, 5, WB.3)    |                 |

- If a register reads and writes to the same register in the same cycle, is it a RAW / WAR?
	- (1, 5, RR.3)    (3, 5, WB.3)
- Which hazard???
- **Simulate on practical.**
- WAR Hazard ? --  RR.5(i4,c14)) WB.5,(i1,c14)
- ???     Hazard ? -- RR.3(i1, c5)  WB.3(i3, c5)

### A(iii)

| Hazard Type | 1st Instruction | 2nd Instruction | 3rd Instruction |
| ----------- | --------------- | --------------- | --------------- |
| Structural  | (2, 4, RR.3)    | (3, 4, RR.5)    | (4, 4, RR.7)    |
| Structural  | (1, 6, IALU)    | (2, 6, IALU)    | (4, 6, IALU)    |
| Structural  | (3, 6, FALU)    | (6, 6, FALU)    |                 |
| Structural  | (2, 8, WB.4)    | (6, 8, WB.12)   |                 |
| Memory      | (1, 7, DS)      | (2, 7, DF)      | (5, 7, OF)                |

- Is final memory hazard valid???
- Is it memory or DATA
- 2 Memory read ports?


## Part B

### B(i)


| Instr. |     |     |     |      |      |      |      |      |      |      |      |                     |
| ------ | --- | --- | --- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ------------------- |
| 1      | IF  | ID  | OF  | RR.2 | RR.3 | IALU | IALU | DS   |      |      |      |                     |
| 2      |     | IF  | ID  | OF   | ---  | WB.3 |      |      |      |      |      |                     |
| 3      |     |     | --- | ---  | IF   | ID   | RR.4 | IALU | IALU | WB.5 |      |                     |
| 4      |     |     |     | ---  | ---  | IF   | ID   | RR.2 | IALU | ---  | WB.2 |                     |
|        | 1   | 2   | 3   | 4    | 5    | 6    | 7    | 8    | 9    | 10   | 11   | $\leftarrow$ cycle |


### B(ii)

| Instr. |     |     |     |      |      |      |      |      |      |      |      |                    |
| ------ | --- | --- | --- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ------------------ |
| 1      | IF  | ID  | OF  | RR.2 | RR.3 | IALU | IALU | DS   |      |      |      |                    |
| 2      |     | NOP |     |      |      |      |      |      |      |      |      |                    |
| 3      |     |     | NOP |      |      |      |      |      |      |      |      |                    |
| 4      |     |     |     | IF   | ID   | OF   | WB.3 |      |      |      |      |                    |
| 5      |     |     |     |      | IF   | ID   | RR.4 | IALU | IALU | WB.5 |      |                    |
| 6      |     |     |     |      |      | NOP  |      |      |      |      |      |                    |
| 7      |     |     |     |      |      |      | IF   | ID   | RR.2 | IALU | WB.2 |                    |
|        | 1   | 2   | 3   | 4    | 5    | 6    | 7    | 8    | 9    | 10   | 11   | $\leftarrow$ cycle |


### B(iii)

| Instr. |     |     |      |      |       |       |      |       |       |      |      |                    |
| ------ | --- | --- | ---- | ---- | ----- | ----- | ---- | ----- | ----- | ---- | ---- | ------------------ |
| 1      | IF  | ID  | RR.1 | RR.2 | IALU  | WB.3  |      |       |       |      |      |                    |
| 2      |     | IF  | ID   | OF   | WB.13 | IALU  | IALU | IALU  | WB.5  |      |      |                    |
| 3      |     |     | IF   | ID   | RR.4  | IALU  | IALU | WB.15 |       |      |      |                    |
| 4      |     |     |      | IF   | ID    | RR.13 | IALU | WB.2  |       |      |      |                    |
| 5      |     |     |      |      | IF    | ID    | OF   | RR.9  | RR.15 | IALU | WB.2 |                    |
| 6      |     |     |      |      |       | IF    | ID   | WB.19 |       |      |      |                    |
|        | 1   | 2   | 3    | 4    | 5     | 6     | 7    | 8     | 9     | 10   | 11   | $\leftarrow$ cycle           |

- **Still has memory hazards:** (2,4,0F) (4,4,IF)

## Part C

### C(i)

| Test Case | Serial cycles | Pipelined cycles (hazards) | Pipelined cycles (hazards resolved) | Speedup (hazards) | Speedup (hazards resolved) |
| --------- | ------------- | -------------------------- | ----------------------------------- | ----------------- | -------------------------- |
| B(i)      | 23            | 8                          | 11                                  | 2.9               | 2.1                        |
| B(ii)     | 23            | 8                          | 11                                  | 2.9               | 2.1                        |
| B(iii)    | 35            | 11                         | 11                                  | 3.2               | 3.2                           |

- Example gives the number of cycles without hazards $\lt$ number of cycles with hazards
	- Resolving hazards should always take more cycles?
	- Inserting stalls/NOP should increase number of cycles or stay the same.

### C(ii)

**(a) RAW:** An instruction $I_1$ intends to write to a register $R$. However, before the W.B cycle is executed, a later pipelined instruction, $I_2$ reads $R$. This causes $I_2$ to have an outdated version of $R$, not the value that would be written from $I_1$.

Solution: Insert stalls before the R.R cycle in $I_2$ until it is executed the cycle after the W.B.

**(b) WAR:** An instruction $I_1$ intends to read a register $R$. However, before the R.R cycle is executed, a later pipelined instruction $I_2$ writes a new value to $R$. This causes $I_1$ to read the new incorrect value of $R$, rather than the expected that $I_1$ would read the value in $R$ before either instruction was executed.

Solution: Insert non-dependant instructions between the read and write instructions, such that the write instruction occurs at least a cycle after the read instruction. If no non-dependant instructions exist in this particular context, insert NOP instructions.

**(c) WAW:** Instructions $I_{1}, I_{2}$ intend to write to register $R$, such that instruction $I_1$ is executed before $I_2$. A WAW hazard occurs when $I_2$ executes its W.B cycle before $I_1$, causing the value from $I_2$ to be overwritten by the outdated value from $I_1$, when $I_1$ executes its W.B cycle.

Solution: Operand forwarding with Tomasulo algorithm, which uses register renaming.

Rename the second write instruction register with a new register, and rename any occurrences of that register in instructions after the second write to the new register.


## Part D

### D(i)


> Explain the concept of dependency DAG, and how this dependency DAG graph representation relates to **dependencies** and **register hazards**.
>   - **DAG:** Directed Acyclic Graph.
### D(ii)
> Provide an appropriate example dependency DAG diagram and its associated code, showing and discussing at least two kinds of register hazard.

### D(iii)
> Draw instruction dependency DAG from test case:

TEST CASE:
```
1. LDR R1, R5
2. LDR R5, R6
3. IMUL R3, R6, R8
4. IMUL R1, R4, R4
5. IADD R2, R6, R5
6. IMUL R3, R6, R8
7. IMUL R1, R4, R4
8. IADD R4, R8, R7
```

### Appendix Notes

$O(n^{4}) \rightarrow O(n^{2})$

Only hazards are register & memory based:
1. Loading a register from memory followed by using _that_ register as a source
2. Storing to any memory location followed by loading from any location
3. Loading from memory followed by using _any_ register as the target of an ALU or load/store with address modification

Approach
1. Divide each procedure into basic blocks
2. Construct dependency DAG expressing scheduling constraints within each basic block
3. Schedule instructions in block, guided by applicable heuristics using no lookahead in the graph

DAG
Node: instructions
Edge: Serialization dependencies between instructions

Edge leading from instruction $a$ to instruction $b$ indicates $a$ must be executed before $b$

DAG serializes
- Definitions v definitions
- Definitions v uses
- Uses v definitions

Scan backwards across basic block, noting each definition or use of resource and then later the definitions or uses which must precede it


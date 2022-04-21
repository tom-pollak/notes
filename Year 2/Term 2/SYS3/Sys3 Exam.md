# Sys3 Open Assessment

## Part 

# OF does not cause a memory error !!!!!!!

A Data Hazard can occur when Instruction Fetch (IF) conflicts with a Data Fetch (DF), or data store (DS). This is due to the memory bus only being able to perform one code or data operation per clock cycle. A possible solution is to insert stalls to delay the second of the events and thus separate the conflicting operations into different clock cycles.

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
| Structural  | (3, 8, WB.5)    | (4, 8, WB.2)                |                 |

- If a register reads and writes to the same register in the same cycle, is it a RAW / WAR?
	- (1, 5, RR.3)    (3, 5, WB.3)
- Which hazard???
- **Simulate on practical.**

### A(iii)

| Hazard Type | 1st Instruction | 2nd Instruction | 3rd Instruction |
| ----------- | --------------- | --------------- | --------------- |
| Structural  | (2, 4, RR.3)    | (3, 4, RR.5)    | (4, 4, RR.7)    |
| Structural  | (1, 6, IALU)    | (2, 6, IALU)    | (4, 6, IALU)    |
| Structural  | (3, 6, FALU)    | (6, 6, FALU)    |                 |
| Structural  | (2, 8, WB.4)    | (6, 8, WB.12)   |                 |
| Memory      | (1, 7, DS)      | (2, 7, DF)      | (5, 7, OF)                |

- Is final memory hazard valid???


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


- Still has memory hazards: (2,4,0F) (4,4,IF)

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

**(a) RAW:** An instruction $I_1$ intends to a register, $R$, however before the W.B instruction is issued, a later pipelined instruction $I_2$ reads $R$ before $I_1$ can write to it. This causes $I_2$ to have an incorrect version of $R$.

Solution: Insert stalls into before the read instruction until it is executed the cycle after the write instruction

**(b) WAR:** 

Solution: Insert non-dependant instructions between the read and subsequent write instruction, such that the write instruction occurs at least a cycle after the read instruction. If no non-dependant instructions in this particular context exist, insert NOP instructions.

**(c) WAW:** 

Solution: Register renaming, rename the second write instruction register with a new register, and rename any occurrences of that register in subsequent instructions after the second write to the new register.
